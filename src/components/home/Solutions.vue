<template>
  <section class="py-32 bg-gradient-to-b from-gray-50 to-white relative overflow-hidden">
    <!-- Background decoration -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
      <div class="absolute top-1/4 left-0 w-96 h-96 bg-gradient-to-br from-blue-400/10 to-purple-400/10 rounded-full blur-3xl" />
      <div class="absolute bottom-1/4 right-0 w-96 h-96 bg-gradient-to-br from-purple-400/10 to-pink-400/10 rounded-full blur-3xl" />
    </div>

    <div class="max-w-7xl mx-auto px-6 relative">
      <!-- Header -->
      <div class="text-center mb-20 opacity-animation">
        <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-gradient-to-r from-blue-500/10 to-purple-500/10 border border-purple-200/50 mb-6">
          <span class="text-sm bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
            Комплексное решение
          </span>
        </div>
        <h2 class="text-4xl md:text-6xl mb-6 bg-gradient-to-r from-gray-900 via-purple-900 to-gray-900 bg-clip-text text-transparent">
          Как Career Tracking помогает вам расти
        </h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          7 мощных инструментов для системного развития вашей карьеры
        </p>
      </div>

      <!-- Solutions Grid -->
      <div class="space-y-8">
        <div
            v-for="(solution, index) in solutions"
            :key="index"
            :class="[
            'flex flex-col lg:flex-row gap-8 items-center slide-up-animation',
            index % 2 === 0 ? 'lg:flex-row' : 'lg:flex-row-reverse'
          ]"
            :style="{ animationDelay: `${index * 0.1}s` }"
        >
          <!-- Content -->
          <div class="flex-1 p-8 lg:p-12 rounded-3xl bg-white border border-gray-200 shadow-xl hover:shadow-2xl transition-shadow">
            <div class="flex items-center gap-4 mb-6">
              <div
                  :class="`w-16 h-16 rounded-2xl bg-gradient-to-br ${solution.bgGradient} flex items-center justify-center`"
              >
                <component
                    :is="solution.icon"
                    :class="`w-8 h-8 bg-gradient-to-br ${solution.gradient} bg-clip-text text-transparent`"
                    :style="{ WebkitTextFillColor: 'transparent' }"
                />
              </div>
              <div>
                <span :class="`text-sm bg-gradient-to-r ${solution.gradient} bg-clip-text text-transparent`">
                  Шаг {{ solution.label }}
                </span>
                <h3 class="text-3xl">{{ solution.title }}</h3>
              </div>
            </div>

            <ul class="space-y-4">
              <li v-for="(feature, fIndex) in solution.features" :key="fIndex" class="flex items-start gap-3">
                <div
                    :class="`w-6 h-6 rounded-lg bg-gradient-to-br ${solution.bgGradient} flex items-center justify-center flex-shrink-0 mt-0.5`"
                >
                  <div
                      :class="`w-2 h-2 rounded-full bg-gradient-to-r ${solution.gradient}`"
                  />
                </div>
                <span class="text-gray-700">{{ feature }}</span>
              </li>
            </ul>
          </div>

          <!-- Visual mockup -->
          <div class="flex-1 relative hover:scale-105 transition-transform">
            <div
                :class="`rounded-3xl bg-gradient-to-br ${solution.bgGradient} border border-gray-200 p-8 aspect-square flex items-center justify-center relative overflow-hidden`"
            >
              <!-- Decorative background -->
              <div class="absolute inset-0 opacity-50">
                <div
                    :class="`absolute top-4 right-4 w-32 h-32 rounded-full bg-gradient-to-br ${solution.gradient} opacity-20 blur-2xl`"
                />
                <div
                    :class="`absolute bottom-4 left-4 w-40 h-40 rounded-full bg-gradient-to-br ${solution.gradient} opacity-20 blur-2xl`"
                />
              </div>

              <!-- Icon -->
              <div class="relative">
                <component
                    :is="solution.icon"
                    class="w-32 h-32 text-gray-300"
                    :stroke-width="1"
                />
              </div>

              <!-- Label -->
              <div
                  :class="`absolute top-8 left-8 w-16 h-16 rounded-2xl bg-gradient-to-br ${solution.gradient} flex items-center justify-center shadow-lg`"
              >
                <span class="text-2xl text-white">{{ solution.label }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import {
  FileCheck,
  BarChart3,
  BookText,
  Video,
  Code,
  Briefcase,
  Map
} from 'lucide-vue-next'

const solutions = ref([
  // {
  //   icon: FileCheck,
  //   label: 'A',
  //   title: 'AI-Аудит резюме',
  //   features: [
  //     'Определение текущего уровня специалиста',
  //     'Сильные / слабые стороны',
  //     'Отсутствующие навыки',
  //     'Рекомендации для роста',
  //   ],
  //   gradient: 'from-blue-500 to-cyan-500',
  //   bgGradient: 'from-blue-500/10 to-cyan-500/10',
  // },
  {
    icon: BarChart3,
    label: 'B',
    title: 'Личный дашборд',
    features: [
      'Рост навыков',
      'Еженедельная статистика',
      'Прогресс за месяц',
      'Очки развития',
    ],
    gradient: 'from-purple-500 to-pink-500',
    bgGradient: 'from-purple-500/10 to-pink-500/10',
  },
  {
    icon: BookText,
    label: 'C',
    title: 'Заметки с анализом',
    features: [
      'Пишите заметки 2–3 раза в неделю',
      'Система анализирует что вы сделали',
      'Отслеживает что вы выучили',
      'Показывает изменение уровня навыков',
    ],
    gradient: 'from-emerald-500 to-teal-500',
    bgGradient: 'from-emerald-500/10 to-teal-500/10',
  },
  {
    icon: Video,
    label: 'D',
    title: 'Mock-интервью',
    features: [
      'ИИ проводит тестовое интервью',
      'Технические и HR вопросы',
      'Детальный отчёт по результатам',
      'Рекомендации по улучшению',
    ],
    gradient: 'from-orange-500 to-red-500',
    bgGradient: 'from-orange-500/10 to-red-500/10',
  },
  {
    icon: Code,
    label: 'E',
    title: 'Тесты, задачи и практика',
    features: [
      'Технические тесты',
      'Открытые вопросы',
      'Код-задачи',
      'Повышение уровня после каждого шага',
    ],
    gradient: 'from-indigo-500 to-purple-500',
    bgGradient: 'from-indigo-500/10 to-purple-500/10',
  },
  {
    icon: Briefcase,
    label: 'F',
    title: 'Вакансии',
    features: [
      'Узбекистан + международные',
      'Рекомендованные позиции',
      'Сопоставление навыков с требованиями',
      'Персональные рекомендации',
    ],
    gradient: 'from-cyan-500 to-blue-500',
    bgGradient: 'from-cyan-500/10 to-blue-500/10',
  },
  {
    icon: Map,
    label: 'G',
    title: 'Персональная дорожная карта',
    features: [
      '12-месячный план развития',
      'Месячные чекпоинты',
      'Очки роста',
      'Текущий уровень → следующий уровень',
    ],
    gradient: 'from-pink-500 to-rose-500',
    bgGradient: 'from-pink-500/10 to-rose-500/10',
  },
])
</script>

<style scoped>
@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

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

.slide-up-animation {
  animation: slideUp 0.6s ease-out forwards;
  opacity: 0;
}

.opacity-animation {
  animation: fadeInUp 0.6s ease-out;
}
</style>