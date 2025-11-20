<template>
  <section class="py-40 relative overflow-hidden">

    <!-- Gradient background (updated to match screenshot) -->
    <div
        class="absolute inset-0 bg-gradient-to-br from-blue-500 via-purple-600 to-pink-600"
    />

    <!-- Soft radial lighting like in screenshot -->
    <div class="absolute inset-0">
      <div class="absolute inset-0 bg-gradient-to-br from-blue-400/30 via-purple-500/40 to-pink-500/30 opacity-60 blur-[120px]"></div>
    </div>

    <!-- Floating glowing blobs -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
      <div
          class="absolute top-[-120px] left-[-80px] w-[500px] h-[500px] bg-white/20 rounded-full blur-[140px]"
          :style="{ animation: 'blob 18s infinite' }"
      />
      <div
          class="absolute bottom-[-150px] right-[-80px] w-[550px] h-[550px] bg-white/20 rounded-full blur-[150px]"
          :style="{ animation: 'blob-reverse 22s infinite' }"
      />
    </div>

    <div class="max-w-5xl mx-auto px-6 relative text-center">

      <div
          class="space-y-10"
          :class="{ 'opacity-0 translate-y-7': !isVisible, 'opacity-100 translate-y-0': isVisible }"
          :style="{ transition: 'all 0.7s ease-out' }"
      >
        <!-- Icon container -->
        <div
            class="inline-flex"
            :style="{ animation: 'rotate-gentle 5s infinite' }"
        >
          <div class="w-24 h-24 rounded-3xl bg-white/10 backdrop-blur-md border border-white/30 flex items-center justify-center shadow-xl">
            <Sparkles class="w-12 h-12 text-white" />
          </div>
        </div>

        <!-- Heading -->
        <h2 class="text-5xl md:text-6xl font-semibold text-white tracking-tight">
          Начните свой рост сегодня
        </h2>

        <!-- Description -->
        <p class="text-xl text-white/90 max-w-2xl mx-auto leading-relaxed">
          Ваше будущее — в ваших руках. Получите персональный AI-аудит и
          начните развиваться по индивидуальному плану уже сегодня.
        </p>

        <!-- Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 justify-center pt-10">
          <button
              class="px-10 py-4 rounded-2xl bg-white text-gray-900 flex items-center justify-center gap-2 shadow-2xl hover:shadow-xl transition-all hover:scale-105 active:scale-95"
          >
            Начать бесплатный аудит
            <ArrowRight class="w-5 h-5" />
          </button>

          <button
              class="px-10 py-4 rounded-2xl bg-white/10 backdrop-blur-md border border-white/30 text-white flex items-center justify-center gap-2 hover:bg-white/20 transition-all hover:scale-105 active:scale-95"
          >
            Узнать больше
          </button>
        </div>

        <!-- Stats -->
        <div class="flex flex-col sm:flex-row items-center justify-center gap-12 pt-16 text-white/90">

          <div class="text-center">
            <div class="text-4xl font-semibold text-white mb-1">50,000+</div>
            <div class="text-white/80 text-lg">Активных пользователей</div>
          </div>

          <div class="hidden sm:block w-px h-16 bg-white/25" />

          <div class="text-center">
            <div class="text-4xl font-semibold text-white mb-1">4.9/5</div>
            <div class="text-white/80 text-lg">Средняя оценка</div>
          </div>

          <div class="hidden sm:block w-px h-16 bg-white/25" />

          <div class="text-center">
            <div class="text-4xl font-semibold text-white mb-1">95%</div>
            <div class="text-white/80 text-lg">Достигли своих целей</div>
          </div>

        </div>
      </div>
    </div>

    <!-- Bottom wave (kept original but smoothed slightly) -->
    <div class="absolute bottom-0 left-0 right-0">
      <svg
          class="w-full h-24 text-white"
          preserveAspectRatio="none"
          viewBox="0 0 1200 120"
      >
        <path
            d="M0,50 C300,100 900,0 1200,50 L1200,120 L0,120 Z"
            fill="currentColor"
        />
      </svg>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { ArrowRight, Sparkles } from "lucide-vue-next";

const isVisible = ref(false);

onMounted(() => {
  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        isVisible.value = true;
        observer.unobserve(entry.target);
      }
    });
  });

  observer.observe(document.querySelector("section"));
});
</script>

<style scoped>
@keyframes blob {
  0%, 100% {
    opacity: 0.1;
    transform: scale(1) rotate(0deg);
  }
  50% {
    opacity: 0.25;
    transform: scale(1.25) rotate(90deg);
  }
}

@keyframes blob-reverse {
  0%, 100% {
    opacity: 0.1;
    transform: scale(1) rotate(0deg);
  }
  50% {
    opacity: 0.25;
    transform: scale(1.3) rotate(-90deg);
  }
}

@keyframes rotate-gentle {
  0%, 100% {
    transform: rotate(0deg);
  }
  50% {
    transform: rotate(12deg);
  }
}
</style>
