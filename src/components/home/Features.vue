<template>
  <section id="features" class="py-32 bg-gradient-to-b from-gray-50 to-white relative overflow-hidden">
    <!-- Background decoration -->
    <div class="absolute top-0 left-1/2 -translate-x-1/2 w-full h-96 bg-gradient-to-b from-purple-100/50 to-transparent blur-3xl" />

    <div class="max-w-7xl mx-auto px-6 relative">
      <!-- Header -->
      <div
          v-intersection-observer="handleHeaderIntersect"
          class="text-center mb-20 transition-all duration-600"
          :class="headerVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-5'"
      >
        <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-gradient-to-r from-purple-500/10 to-pink-500/10 border border-purple-200/50 mb-6">
          <span class="text-sm bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent">
            Полный набор инструментов
          </span>
        </div>
        <h2 class="text-4xl md:text-5xl mb-6 bg-gradient-to-r from-gray-900 to-gray-600 bg-clip-text text-transparent">
          Основные функции
        </h2>
        <p class="text-xl text-gray-600 max-w-2xl mx-auto">
          Всё необходимое для системного карьерного роста в одной платформе
        </p>
      </div>

      <!-- Features Grid -->
      <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-6">
        <div
            v-for="(feature, index) in features"
            :key="index"
            v-intersection-observer="(entries) => handleFeatureIntersect(entries, index)"
            class="group relative p-8 rounded-3xl bg-white border border-gray-200 shadow-lg hover:shadow-2xl transition-all duration-500 cursor-pointer feature-card"
            :class="visibleFeatures[index] ? 'opacity-100 scale-100' : 'opacity-0 scale-90'"
            :style="{ 'transition-delay': `${index * 50}ms` }"
        >
          <!-- Gradient background on hover -->
          <div
              :class="`absolute inset-0 rounded-3xl bg-gradient-to-br ${feature.gradient} opacity-0 group-hover:opacity-5 transition-opacity`"
          />

          <div class="relative">
            <!-- Icon -->
            <div
                :class="`w-14 h-14 rounded-2xl bg-gradient-to-br ${feature.gradient} bg-opacity-10 flex items-center justify-center mb-6 group-hover:scale-110 transition-transform`"
            >
              <component
                  :is="feature.icon"
                  :class="`w-7 h-7 bg-gradient-to-br ${feature.gradient} bg-clip-text`"
                  :style="{ color: 'transparent', WebkitTextFillColor: 'transparent', backgroundImage: `linear-gradient(to bottom right, var(--tw-gradient-stops))` }"
              />
            </div>

            <!-- Content -->
            <h3 class="text-xl mb-3">{{ feature.title }}</h3>
            <p class="text-gray-600 text-sm leading-relaxed">{{ feature.description }}</p>
          </div>

          <!-- Corner accent -->
          <div
              :class="`absolute top-0 right-0 w-20 h-20 bg-gradient-to-br ${feature.gradient} opacity-0 group-hover:opacity-10 rounded-3xl blur-2xl transition-opacity`"
          />
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
  FileText,
  Map,
  Briefcase,
} from 'lucide-vue-next'

const headerVisible = ref(false)
const visibleFeatures = ref({})

const features = [
  {
    icon: FileCheck,
    title: 'AI-Аудит резюме',
    description: 'Глубокий анализ вашего опыта и навыков с персональными рекомендациями',
    gradient: 'from-blue-500 to-cyan-500',
  },
  {
    icon: BarChart3,
    title: 'Дашборд роста',
    description: 'Визуализация прогресса, статистика и аналитика вашего развития',
    gradient: 'from-purple-500 to-pink-500',
  },
  {
    icon: BookText,
    title: 'Анализ заметок',
    description: 'ИИ обрабатывает ваши записи и выявляет паттерны роста',
    gradient: 'from-emerald-500 to-teal-500',
  },
  {
    icon: Video,
    title: 'Mock-интервью',
    description: 'Практика технических и HR интервью с детальной обратной связью',
    gradient: 'from-orange-500 to-red-500',
  },
  {
    icon: Code,
    title: 'Тесты + код-задачи',
    description: 'Практические задания для проверки и развития навыков',
    gradient: 'from-indigo-500 to-purple-500',
  },
  {
    icon: FileText,
    title: 'Отчёты за месяц',
    description: 'Подробные месячные отчёты о достижениях и прогрессе',
    gradient: 'from-cyan-500 to-blue-500',
  },
  {
    icon: Map,
    title: 'Персональная дорожная карта',
    description: '12-месячный план с чёткими целями и чекпоинтами',
    gradient: 'from-pink-500 to-rose-500',
  },
  {
    icon: Briefcase,
    title: 'Подбор вакансий',
    description: 'Релевантные вакансии с анализом соответствия навыков',
    gradient: 'from-violet-500 to-purple-500',
  },
]

const handleHeaderIntersect = (entries) => {
  if (entries[0].isIntersecting) {
    headerVisible.value = true
  }
}

const handleFeatureIntersect = (entries, index) => {
  if (entries[0].isIntersecting) {
    visibleFeatures.value[index] = true
  }
}

// Custom directive for intersection observer
const vIntersectionObserver = {
  mounted(el, binding) {
    const observer = new IntersectionObserver(
        (entries) => {
          binding.value(entries)
        },
        { threshold: 0.1 }
    )
    observer.observe(el)
    el._observer = observer
  },
  unmounted(el) {
    if (el._observer) {
      el._observer.disconnect()
    }
  },
}
</script>

<style scoped>
.feature-card {
  will-change: transform, opacity;
}

.feature-card:hover {
  transform: translateY(-8px);
}
</style>