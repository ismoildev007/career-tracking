<template>
  <section id="testimonials" class="py-32 bg-gradient-to-b from-white to-gray-50 relative overflow-hidden">
    <!-- Background elements -->
    <div class="absolute top-20 right-0 w-96 h-96 bg-gradient-to-br from-purple-400/10 to-pink-400/10 rounded-full blur-3xl" />
    <div class="absolute bottom-20 left-0 w-96 h-96 bg-gradient-to-br from-blue-400/10 to-cyan-400/10 rounded-full blur-3xl" />

    <div class="max-w-7xl mx-auto px-6 relative">
      <div class="text-center mb-20 animate-fade-in-up">
        <h2 class="text-4xl md:text-5xl mb-6 bg-gradient-to-r from-gray-900 to-gray-600 bg-clip-text text-transparent">
          Настоящие люди. Настоящий рост.
        </h2>
        <p class="text-xl text-gray-600 max-w-2xl mx-auto">
          Истории успеха наших пользователей
        </p>
      </div>

      <div class="grid md:grid-cols-2 gap-8">
        <div
            v-for="(testimonial, index) in testimonials"
            :key="index"
            class="group relative p-8 rounded-3xl bg-white border border-gray-200 shadow-lg hover:shadow-2xl transition-all hover:-translate-y-2"
            :style="{ animationDelay: `${index * 0.1}s` }"
        >
          <!-- Rating stars -->
          <div class="flex gap-1 mb-6">
            <Star
                v-for="i in 5"
                :key="i"
                class="w-5 h-5 fill-yellow-400 text-yellow-400"
            />
          </div>

          <!-- Testimonial text -->
          <p class="text-gray-700 mb-8 leading-relaxed">{{ testimonial.text }}</p>

          <!-- Author info -->
          <div class="flex items-center gap-4">
            <div class="relative">
              <div
                  :class="`absolute inset-0 rounded-full bg-gradient-to-br ${testimonial.gradient} opacity-20 blur-lg`"
              />
              <img
                  :src="testimonial.image"
                  :alt="testimonial.name"
                  class="relative w-16 h-16 rounded-full object-cover border-2 border-white"
              />
            </div>
            <div class="flex-1">
              <div class="mb-1 font-medium">{{ testimonial.name }}</div>
              <div class="text-sm text-gray-500">{{ testimonial.role }}</div>
            </div>
          </div>

          <!-- Progress badge -->
          <div
              :class="`mt-6 inline-flex items-center gap-2 px-4 py-2 rounded-full bg-gradient-to-r ${testimonial.gradient} bg-opacity-10`"
          >
            <TrendingUp class="w-4 h-4 text-green-600" />
            <span class="text-sm">{{ testimonial.progress }}</span>
          </div>

          <!-- Decorative corner -->
          <div
              :class="`absolute top-0 right-0 w-32 h-32 bg-gradient-to-br ${testimonial.gradient} opacity-0 group-hover:opacity-5 rounded-3xl blur-2xl transition-opacity`"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Star, TrendingUp } from 'lucide-vue-next'

const testimonials = [
  {
    name: 'Алексей Петров',
    role: 'Frontend Developer',
    image: 'https://images.unsplash.com/photo-1752859951149-7d3fc700a7ec?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHx0ZWNoJTIwcHJvZmVzc2lvbmFsJTIwcG9ydHJhaXR8ZW58MXx8fHwxNzYzNTYzMTQ0fDA&ixlib=rb-4.1.0&q=80&w=1080',
    text: 'Career Tracking изменил мой подход к развитию. Впервые я увидел чёткий план и смог отслеживать реальный прогресс. За 4 месяца перешёл на новую позицию с повышением зарплаты на 60%.',
    progress: '+40% рост навыков',
    gradient: 'from-blue-500 to-cyan-500',
  },
  {
    name: 'Мария Соколова',
    role: 'Product Manager',
    image: 'https://images.unsplash.com/photo-1762341116897-921e2a52f7ff?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxidXNpbmVzcyUyMHdvbWFuJTIwY29uZmlkZW50fGVufDF8fHx8MTc2MzYyMTUzNXww&ixlib=rb-4.1.0&q=80&w=1080',
    text: 'Платформа помогла мне структурировать знания и заполнить пробелы. Mock-интервью были настолько реалистичными, что на реальном собеседовании я чувствовала себя уверенно. Результат — оффер от международной компании.',
    progress: 'Новая работа за 3 месяца',
    gradient: 'from-purple-500 to-pink-500',
  },
  {
    name: 'Дмитрий Иванов',
    role: 'Backend Developer',
    image: 'https://images.unsplash.com/photo-1752859951149-7d3fc700a7ec?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxkZXZlbG9wZXIlMjBtYW4lMjBwb3J0cmFpdHxlbnwxfHx8fDE3NjM2MjE1MzZ8MA&ixlib=rb-4.1.0&q=80&w=1080',
    text: 'Раньше я не знал, как измерить свой прогресс. Теперь у меня есть дашборд с чёткими метриками. Система тестов и код-задач помогла подготовиться к техническим интервью. Прошёл 5 из 6 собеседований.',
    progress: 'Уверенность в технических интервью',
    gradient: 'from-emerald-500 to-teal-500',
  },
  {
    name: 'Анна Волкова',
    role: 'UX Designer',
    image: 'https://images.unsplash.com/photo-1762341116897-921e2a52f7ff?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxidXNpbmVzcyUyMHdvbWFuJTIwY29uZmlkZW50fGVufDF8fHx8MTc2MzYyMTUzNXww&ixlib=rb-4.1.0&q=80&w=1080',
    text: 'AI-аудит показал мне слабые стороны, о которых я даже не подозревала. Дорожная карта была настолько точной и персонализированной, что я следовала ей месяц за месяцем. Теперь я Senior Designer.',
    progress: '+50% рост за 6 месяцев',
    gradient: 'from-orange-500 to-red-500',
  },
]
</script>

<style scoped>
@keyframes fade-in-up {
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
  animation: fade-in-up 0.6s ease-out forwards;
}
</style>