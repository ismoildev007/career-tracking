<template>
  <section id="how-it-works" class="py-32 bg-gradient-to-b from-white to-gray-50">
    <div class="max-w-7xl mx-auto px-6">
      <!-- Header -->
      <div class="text-center mb-20 animate-fade-in-up">
        <h2 class="text-4xl md:text-5xl mb-6 bg-gradient-to-r from-gray-900 to-gray-600 bg-clip-text text-transparent">
          Как это работает
        </h2>
        <p class="text-xl text-gray-600 max-w-2xl mx-auto">
          4 простых шага до вашего карьерного роста
        </p>
      </div>

      <!-- Steps Grid -->
      <div class="relative">
        <!-- Connection line -->
        <div class="hidden lg:block absolute top-1/2 left-0 right-0 h-1 bg-gradient-to-r from-blue-200 via-purple-200 to-cyan-200 -translate-y-1/2" />

        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8 relative">
          <div
              v-for="(step, index) in steps"
              :key="index"
              class="relative animate-fade-in-up"
              :style="{ animationDelay: `${index * 0.15}s` }"
          >
            <div class="bg-white rounded-3xl p-8 border border-gray-200 shadow-lg hover:shadow-2xl transition-all hover:-translate-y-2">
              <!-- Number badge -->
              <div class="absolute -top-4 -right-4 w-12 h-12 rounded-2xl bg-gradient-to-br from-blue-600 to-purple-600 flex items-center justify-center shadow-lg">
                <span class="text-white text-sm">{{ step.number }}</span>
              </div>

              <!-- Icon -->
              <div class="w-16 h-16 rounded-2xl bg-gradient-to-br from-blue-500/10 to-purple-500/10 flex items-center justify-center mb-6">
                <component :is="step.icon" class="w-8 h-8 text-purple-600" />
              </div>

              <h3 class="text-xl mb-3">{{ step.title }}</h3>
              <p class="text-gray-600">{{ step.description }}</p>
            </div>

            <!-- Arrow for mobile -->
            <div v-if="index < steps.length - 1" class="lg:hidden flex justify-center my-4">
              <div class="w-1 h-8 bg-gradient-to-b from-blue-200 to-purple-200" />
            </div>
          </div>
        </div>
      </div>

      <!-- CTA Button -->
      <div class="text-center mt-16 animate-fade-in-up" style="animationDelay: 0.6s">
        <button class="px-8 py-4 rounded-2xl bg-gradient-to-r from-blue-600 to-purple-600 text-white hover:shadow-xl transition-shadow">
          Начать прямо сейчас
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Upload, Sparkles, Map, TrendingUp } from 'lucide-vue-next'

const steps = [
  {
    number: '01',
    icon: Upload,
    title: 'Загрузите резюме',
    description: 'Просто загрузите своё резюме в любом формате — PDF, Word или текст',
  },
  {
    number: '02',
    icon: Sparkles,
    title: 'Получите AI-аудит',
    description: 'ИИ проанализирует ваш опыт, навыки и определит текущий уровень',
  },
  {
    number: '03',
    icon: Map,
    title: 'Получите персональный план роста',
    description: 'Система создаст индивидуальную дорожную карту на 12 месяцев',
  },
  {
    number: '04',
    icon: TrendingUp,
    title: 'Развивайтесь и отслеживайте прогресс',
    description: 'Выполняйте задания, сдавайте тесты и наблюдайте свой рост в реальном времени',
  },
]
</script>

<style scoped>
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in-up {
  animation: fadeInUp 0.5s ease-out forwards;
  opacity: 0;
}
</style>