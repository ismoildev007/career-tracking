<template>
  <section id="pricing" class="py-32 bg-gradient-to-b from-gray-50 to-white relative overflow-hidden">
    <!-- Background decoration -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
      <div class="absolute top-0 left-1/4 w-96 h-96 bg-gradient-to-br from-blue-400/10 to-purple-400/10 rounded-full blur-3xl" />
      <div class="absolute bottom-0 right-1/4 w-96 h-96 bg-gradient-to-br from-purple-400/10 to-pink-400/10 rounded-full blur-3xl" />
    </div>

    <div class="max-w-7xl mx-auto px-6 relative">
      <!-- Header -->
      <div class="text-center mb-20 fade-in-up" ref="headerRef">
        <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-gradient-to-r from-purple-500/10 to-pink-500/10 border border-purple-200/50 mb-6">
          <span class="text-sm bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent">
            Простые и прозрачные цены
          </span>
        </div>
        <h2 class="text-4xl md:text-5xl mb-6 bg-gradient-to-r from-gray-900 to-gray-600 bg-clip-text text-transparent">
          Выберите свой план
        </h2>
        <p class="text-xl text-gray-600 max-w-2xl mx-auto">
          Начните бесплатно или выберите план для максимального роста
        </p>
      </div>

      <!-- Plans Grid -->
      <div class="grid md:grid-cols-3 gap-8 items-start">
        <div
            v-for="(plan, index) in plans"
            :key="index"
            class="fade-in-up pricing-card"
            :style="{ animationDelay: `${index * 100}ms` }"
            :class="{ 'lg:scale-105': plan.popular }"
        >
          <div
              class="relative p-8 rounded-3xl bg-white border-2 shadow-xl hover:shadow-2xl transition-all duration-300"
              :class="plan.popular ? 'border-purple-600' : 'border-gray-200'"
              @mouseenter="hoveredCard = index"
              @mouseleave="hoveredCard = null"
              :style="hoveredCard === index ? { transform: 'translateY(-8px) scale(1.02)' } : {}"
          >
            <!-- Popular badge -->
            <div v-if="plan.popular" class="absolute -top-4 left-1/2 -translate-x-1/2">
              <div class="px-4 py-1 rounded-full bg-gradient-to-r from-blue-600 to-purple-600 text-white text-sm shadow-lg">
                Популярный
              </div>
            </div>

            <!-- Icon -->
            <div
                class="w-16 h-16 rounded-2xl flex items-center justify-center mb-6"
                :class="plan.bgGradient"
            >
              <component
                  :is="plan.iconComponent"
                  class="w-8 h-8 text-transparent"
                  :style="{ backgroundImage: `linear-gradient(135deg, var(--gradient-from) 0%, var(--gradient-to) 100%)`, WebkitBackgroundClip: 'text', WebkitTextFillColor: 'transparent' }"
              />
            </div>

            <!-- Plan name -->
            <h3 class="text-2xl mb-2 font-semibold">{{ plan.name }}</h3>
            <p class="text-gray-600 text-sm mb-6">{{ plan.description }}</p>

            <!-- Price -->
            <div class="mb-6">
              <div class="flex items-baseline gap-2">
                <span
                    class="text-5xl font-bold bg-clip-text text-transparent"
                    :class="plan.gradientClass"
                >
                  ${{ plan.price }}
                </span>
                <span v-if="plan.price !== '0'" class="text-gray-500">/ месяц</span>
              </div>
              <div class="text-sm text-gray-500 mt-1">{{ plan.period }}</div>
            </div>

            <!-- CTA Button -->
            <button
                class="w-full px-6 py-4 rounded-2xl mb-8 transition-all duration-200 font-semibold"
                :class="
                plan.popular
                  ? `${plan.gradientClass} text-white shadow-lg hover:shadow-xl`
                  : 'bg-gray-100 text-gray-900 hover:bg-gray-200'
              "
                @click="handleCTA(plan.name)"
            >
              {{ plan.cta }}
            </button>

            <!-- Features -->
            <ul class="space-y-4">
              <li v-for="(feature, fIndex) in plan.features" :key="fIndex" class="flex items-start gap-3">
                <div
                    class="w-5 h-5 rounded-lg flex items-center justify-center flex-shrink-0 mt-0.5"
                    :class="plan.bgGradient"
                >
                  <Check class="w-3 h-3 text-gray-700" />
                </div>
                <span class="text-gray-700 text-sm">{{ feature }}</span>
              </li>
            </ul>

            <!-- Decorative gradient -->
            <div
                class="absolute top-0 right-0 w-40 h-40 opacity-0 hover:opacity-5 rounded-3xl blur-3xl transition-opacity pointer-events-none"
                :class="plan.bgGradient"
            />
          </div>
        </div>
      </div>

      <!-- Footer text -->
      <div class="text-center mt-12 fade-in-up" ref="footerRef">
        <p class="text-gray-600">
          Все планы включают 14-дневную гарантию возврата денег
        </p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import { Check, Sparkles, Crown, Zap } from 'lucide-vue-next'

const hoveredCard = ref(null)
const headerRef = ref(null)
const footerRef = ref(null)

const plans = [
  {
    name: 'Free',
    price: '0',
    period: 'Бесплатно навсегда',
    description: 'Для первого знакомства с платформой',
    icon: 'Sparkles',
    iconComponent: Sparkles,
    gradient: 'from-gray-500 to-gray-600',
    bgGradient: 'bg-gradient-to-br from-gray-500/10 to-gray-600/10',
    gradientClass: 'bg-gradient-to-r from-gray-500 to-gray-600',
    features: [
      'Базовый AI-аудит резюме',
      'Просмотр дорожной карты',
      '1 mock-интервью в месяц',
      'Доступ к 5 тестам',
      'Базовая аналитика',
    ],
    cta: 'Начать бесплатно',
    popular: false,
  },
  {
    name: 'Standard',
    price: '29',
    period: 'в месяц',
    description: 'Для системного развития карьеры',
    icon: 'Zap',
    iconComponent: Zap,
    gradient: 'from-blue-600 to-purple-600',
    bgGradient: 'bg-gradient-to-br from-blue-500/10 to-purple-500/10',
    gradientClass: 'bg-gradient-to-r from-blue-600 to-purple-600',
    features: [
      'Полный AI-аудит резюме',
      'Персональная дорожная карта на 12 месяцев',
      'Анализ заметок (без ограничений)',
      '5 mock-интервью в месяц',
      'Все технические тесты',
      'Детальная аналитика и отчёты',
      'Email поддержка',
    ],
    cta: 'Попробовать Standard',
    popular: true,
  },
  {
    name: 'Premium',
    price: '59',
    period: 'в месяц',
    description: 'Максимальный рост и все возможности',
    icon: 'Crown',
    iconComponent: Crown,
    gradient: 'from-purple-600 to-pink-600',
    bgGradient: 'bg-gradient-to-br from-purple-500/10 to-pink-500/10',
    gradientClass: 'bg-gradient-to-r from-purple-600 to-pink-600',
    features: [
      'Всё из Standard +',
      'Безлимитные mock-интервью',
      'Код-задачи с проверкой',
      'Персональный подбор вакансий',
      'Приоритетная поддержка 24/7',
      'Еженедельные 1-on-1 сессии с ментором',
      'Доступ к закрытому сообществу',
      'Сертификаты после прохождения модулей',
    ],
    cta: 'Начать с Premium',
    popular: false,
  },
]

const handleCTA = (planName) => {
  console.log(`Selected plan: ${planName}`)
}
</script>

<style scoped>
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in-up {
  animation: fadeInUp 0.6s ease-out forwards;
  opacity: 0;
}

.pricing-card {
  transition: all 0.3s ease;
}

.pricing-card:hover {
  transform: translateY(-8px);
}
</style>