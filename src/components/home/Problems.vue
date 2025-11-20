<template>
  <section class="py-32 bg-gradient-to-b from-white to-gray-50">
    <div class="max-w-7xl mx-auto px-6">
      <!-- Header Section -->
      <div
          ref="headerElement"
          class="text-center mb-16"
          :class="{ 'animate-fade-in-up': headerVisible }"
      >
        <h2
            class="text-4xl md:text-5xl mb-6 bg-gradient-to-r from-gray-900 to-gray-600 bg-clip-text text-transparent"
        >
          Почему сложно расти в карьере?
        </h2>
        <p class="text-xl text-gray-600 max-w-2xl mx-auto">
          Большинство специалистов сталкиваются с этими проблемами
        </p>
      </div>

      <!-- Problems Grid -->
      <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
        <div
            v-for="(problem, index) in problems"
            :key="index"
            class="p-8 rounded-3xl bg-white border border-gray-200 shadow-lg hover:shadow-2xl transition-all hover:-translate-y-2 hover:scale-102"
            :style="{
            animation: cardsVisible
              ? `fadeInUp 0.5s ease-out ${index * 0.1}s both`
              : 'none',
          }"
        >
          <div
              class="w-14 h-14 rounded-2xl bg-gradient-to-br from-red-500/10 to-orange-500/10 flex items-center justify-center mb-6"
          >
            <component :is="problem.icon" class="w-7 h-7 text-red-600" />
          </div>
          <h3 class="text-xl mb-3">{{ problem.title }}</h3>
          <p class="text-gray-600">{{ problem.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import {
  Target,
  MessageSquareOff,
  TrendingDown,
  Calendar,
} from 'lucide-vue-next'

const problems = [
  {
    icon: Target,
    title: 'Нет чёткого плана развития',
    description: 'Не понятно, куда двигаться дальше и какие навыки прокачивать',
  },
  {
    icon: MessageSquareOff,
    title: 'Нет эксперта, который даст честную обратную связь',
    description: 'Сложно получить объективную оценку своих сильных и слабых сторон',
  },
  {
    icon: TrendingDown,
    title: 'Невозможно измерить прогресс',
    description: 'Не ясно, растёте ли вы на самом деле или топчетесь на месте',
  },
  {
    icon: Calendar,
    title: 'Нет структуры и регулярной практики',
    description: 'Развитие идет хаотично, без системы и постоянства',
  },
]

const headerVisible = ref(false)
const cardsVisible = ref(false)
const headerElement = ref(null)

onMounted(() => {
  const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            if (entry.target === headerElement.value) {
              headerVisible.value = true
            }
            cardsVisible.value = true
            observer.unobserve(entry.target)
          }
        })
      },
      { threshold: 0.1 }
  )

  if (headerElement.value) {
    observer.observe(headerElement.value)
  }
})
</script>

<style scoped>
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in-up {
  animation: slideIn 0.6s ease-out;
}
</style>