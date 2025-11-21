<template>
  <div class="min-h-screen bg-gradient-to-br from-blue-50 to-purple-50 flex items-center justify-center p-4">
    <div class="w-full max-w-md bg-white rounded-3xl shadow-2xl p-12">
      <div class="flex items-center gap-2 mb-8 justify-center">
        <svg class="w-8 h-8 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"/>
        </svg>
        <span class="text-xl font-semibold">CareerTrack</span>
      </div>

      <div class="text-center mb-8">
        <div class="w-16 h-16 bg-blue-100 rounded-full flex items-center justify-center mx-auto mb-4">
          <svg class="w-8 h-8 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
          </svg>
        </div>
        <h1 class="text-3xl font-bold mb-2">Email tasdiqlash</h1>
        <p class="text-gray-600">
          Emailingizga 6 xonali tasdiqlash kodi yuborildi
        </p>
      </div>

      <form @submit.prevent="handleSubmit" class="space-y-6">
        <div class="flex gap-2 justify-center">
          <input
              v-for="(digit, index) in code"
              :key="index"
              :id="`code-${index}`"
              :ref="el => { if (el) inputRefs[index] = el }"
              type="text"
              inputmode="numeric"
              maxlength="1"
              :value="digit"
              @input="handleChange(index, $event)"
              @keydown="handleKeyDown(index, $event)"
              @paste="handlePaste"
              class="w-12 h-12 text-center text-xl border-2 border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent outline-none transition font-semibold"
              required
          />
        </div>

        <button
            type="submit"
            :disabled="!isCodeComplete"
            class="w-full bg-blue-600 text-white py-3 rounded-lg font-medium hover:bg-blue-700 transition disabled:opacity-50 disabled:cursor-not-allowed"
        >
          Tasdiqlash
        </button>

        <div class="text-center">
          <button
              type="button"
              @click="handleResend"
              class="text-sm text-blue-600 hover:underline"
              :disabled="resendCooldown > 0"
          >
            {{ resendCooldown > 0 ? `Qayta jo'natish (${resendCooldown}s)` : "Kodni qayta jo'natish" }}
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onBeforeUnmount } from 'vue';
import router from "@/router/index.js";

// Emits
const emit = defineEmits(['verify', 'navigate']);

// Reactive data
const code = ref(['', '', '', '', '', '']);
const inputRefs = ref([]);
const resendCooldown = ref(0);
let cooldownInterval = null;

// Computed
const isCodeComplete = computed(() => {
  return code.value.every(digit => digit !== '');
});

const fullCode = computed(() => {
  return code.value.join('');
});

// Methods
const handleChange = (index, event) => {
  const value = event.target.value;

  // Faqat raqamlarni qabul qilish
  if (!/^[0-9]*$/.test(value)) {
    event.target.value = code.value[index];
    return;
  }

  if (value.length <= 1) {
    code.value[index] = value;

    // Auto-focus keyingi inputga
    if (value && index < 5) {
      inputRefs.value[index + 1]?.focus();
    }
  }
};

const handleKeyDown = (index, event) => {
  // Backspace bosilganda oldingi inputga o'tish
  if (event.key === 'Backspace' && !code.value[index] && index > 0) {
    inputRefs.value[index - 1]?.focus();
  }

  // Arrow keys bilan navigatsiya
  if (event.key === 'ArrowLeft' && index > 0) {
    inputRefs.value[index - 1]?.focus();
  }
  if (event.key === 'ArrowRight' && index < 5) {
    inputRefs.value[index + 1]?.focus();
  }
};

const handlePaste = (event) => {
  event.preventDefault();
  const pastedData = event.clipboardData.getData('text');
  const digits = pastedData.replace(/\D/g, '').slice(0, 6).split('');

  digits.forEach((digit, index) => {
    if (index < 6) {
      code.value[index] = digit;
    }
  });

  // Oxirgi to'ldirilgan inputga focus
  const lastFilledIndex = Math.min(digits.length - 1, 5);
  inputRefs.value[lastFilledIndex]?.focus();
};

const handleSubmit = () => {
  if (!isCodeComplete.value) {
    return;
  }

  emit('verify', fullCode.value);
  emit('navigate', '/onboarding');

  // Vue Router bilan ishlatish uchun:
  // import { useRouter } from 'vue-router'
  // const router = useRouter()
  localStorage.setItem('token', 1234567)
  window.location.href = '/onboarding';

  console.log('Verification code submitted:', fullCode.value);
};

const handleResend = () => {
  if (resendCooldown.value > 0) {
    return;
  }

  // Kodni tozalash
  code.value = ['', '', '', '', '', ''];
  inputRefs.value[0]?.focus();

  // Mock resend functionality
  alert('Tasdiqlash kodi qayta yuborildi!');

  // 60 soniyalik cooldown
  resendCooldown.value = 60;
  cooldownInterval = setInterval(() => {
    resendCooldown.value--;
    if (resendCooldown.value <= 0) {
      clearInterval(cooldownInterval);
    }
  }, 1000);

  emit('resend');
};

// Lifecycle
onMounted(() => {
  // Birinchi inputga focus
  inputRefs.value[0]?.focus();
});

onBeforeUnmount(() => {
  if (cooldownInterval) {
    clearInterval(cooldownInterval);
  }
});
</script>

<style scoped>
/* Input animation */
input:focus {
  transform: scale(1.05);
}

input {
  transition: all 0.2s ease;
}

/* Number input spin buttons ni yashirish */
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type="number"] {
  -moz-appearance: textfield;
}

/* Animation for filled inputs */
input:not(:placeholder-shown) {
  background-color: #eff6ff;
  border-color: #3b82f6;
}
</style>