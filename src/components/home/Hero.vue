<template>
  <section class="relative min-h-screen flex items-center justify-center overflow-hidden bg-gradient-to-br from-blue-50 via-purple-50 to-cyan-50">
    <!-- Animated background elements -->
    <div class="absolute inset-0 overflow-hidden">
      <div
          class="absolute top-20 left-20 w-96 h-96 bg-gradient-to-br from-blue-400/30 to-purple-400/30 rounded-full blur-3xl animate-blob"
      />
      <div
          class="absolute bottom-20 right-20 w-96 h-96 bg-gradient-to-br from-purple-400/30 to-cyan-400/30 rounded-full blur-3xl animate-blob-2"
      />
    </div>

    <div class="relative max-w-7xl mx-auto px-6 py-32 grid lg:grid-cols-2 gap-16 items-center">
      <!-- Left side - Content -->
      <div
          class="space-y-8 animate-fade-in-left"
      >
        <div
            class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-white/60 backdrop-blur-sm border border-purple-200/50 animate-fade-in-up"
        >
          <span class="w-2 h-2 rounded-full bg-gradient-to-r from-blue-500 to-purple-500 animate-pulse" />
          <span class="text-sm text-gray-700">Powered by AI</span>
        </div>

        <h1 class="text-5xl md:text-6xl lg:text-7xl bg-gradient-to-r from-gray-900 via-purple-900 to-gray-900 bg-clip-text text-transparent">
          Career Tracking — ваш персональный путь карьерного роста с ИИ
        </h1>

        <p class="text-xl text-gray-600 max-w-2xl">
          Загрузите резюме, получите полный AI-аудит, создайте свой 12-месячный план роста и отслеживайте прогресс каждую неделю.
        </p>

        <div class="flex flex-col sm:flex-row gap-4">
          <button
              class="px-8 py-4 rounded-2xl bg-gradient-to-r from-blue-600 to-purple-600 text-white flex items-center justify-center gap-2 shadow-xl hover:shadow-2xl transition-all hover:scale-105 active:scale-95"
          >
            Начать бесплатный аудит
            <ArrowRight class="w-5 h-5" />
          </button>
          <button
              class="px-8 py-4 rounded-2xl bg-white/80 backdrop-blur-sm border border-gray-200 flex items-center justify-center gap-2 hover:bg-white transition-all hover:scale-105 active:scale-95"
          >
            <Play class="w-5 h-5" />
            Смотреть демо
          </button>
        </div>

        <div class="flex items-center gap-8 pt-8">
          <div>
            <div class="text-3xl bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
              50K+
            </div>
            <div class="text-sm text-gray-600">Пользователей</div>
          </div>
          <div class="w-px h-12 bg-gray-300" />
          <div>
            <div class="text-3xl bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
              95%
            </div>
            <div class="text-sm text-gray-600">Достигли роста</div>
          </div>
          <div class="w-px h-12 bg-gray-300" />
          <div>
            <div class="text-3xl bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
              12M
            </div>
            <div class="text-sm text-gray-600">План развития</div>
          </div>
        </div>
      </div>

      <!-- Right side - Dashboard mockup -->
      <div
          class="relative animate-fade-in-right"
      >
        <div class="relative rounded-3xl overflow-hidden shadow-2xl border border-white/20 bg-white/50 backdrop-blur-xl p-6">
          <img
              src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3Nzg4Nzd8MHwxfHNlYXJjaHwxfHxmdXR1cmlzdGljJTIwZGFzaGJvYXJkJTIwYW5hbHl0aWNzfGVufDF8fHx8MTc2MzYyMTUzNXww&ixlib=rb-4.1.0&q=80&w=1080"
              alt="Career Dashboard"
              class="w-full h-auto rounded-2xl"
          />

          <!-- Floating cards -->
          <div
              class="absolute top-4 right-4 px-4 py-3 rounded-xl bg-white/90 backdrop-blur-sm shadow-lg border border-gray-200/50 animate-float"
          >
            <div class="text-xs text-gray-500">Навыки выросли</div>
            <div class="text-xl bg-gradient-to-r from-green-600 to-emerald-600 bg-clip-text text-transparent">
              +42%
            </div>
          </div>

          <div
              class="absolute bottom-4 left-4 px-4 py-3 rounded-xl bg-white/90 backdrop-blur-sm shadow-lg border border-gray-200/50 animate-float-delayed"
          >
            <div class="text-xs text-gray-500">Следующий уровень</div>
            <div class="text-sm">Senior Developer</div>
          </div>
        </div>

        <!-- Decorative elements -->
        <div class="absolute -z-10 top-10 -right-10 w-72 h-72 bg-gradient-to-br from-purple-400 to-pink-400 rounded-full blur-3xl opacity-20" />
        <div class="absolute -z-10 -bottom-10 -left-10 w-72 h-72 bg-gradient-to-br from-blue-400 to-cyan-400 rounded-full blur-3xl opacity-20" />
      </div>
    </div>
  </section>
</template>

<script setup>
import { ArrowRight, Play } from 'lucide-vue-next'
</script>

<style scoped>
@keyframes blob {
  0%, 100% {
    transform: scale(1) rotate(0deg);
    opacity: 0.3;
  }
  50% {
    transform: scale(1.2) rotate(90deg);
    opacity: 0.5;
  }
}

@keyframes blob-2 {
  0%, 100% {
    transform: scale(1) rotate(0deg);
    opacity: 0.3;
  }
  50% {
    transform: scale(1.3) rotate(-90deg);
    opacity: 0.5;
  }
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}

@keyframes float-delayed {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-15px);
  }
}

@keyframes fade-in-left {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes fade-in-right {
  from {
    opacity: 0;
    transform: translateX(50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

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

.animate-blob {
  animation: blob 20s infinite;
}

.animate-blob-2 {
  animation: blob-2 25s infinite;
}

.animate-float {
  animation: float 3s infinite;
}

.animate-float-delayed {
  animation: float-delayed 4s infinite;
}

.animate-fade-in-left {
  animation: fade-in-left 0.8s ease-out;
}

.animate-fade-in-right {
  animation: fade-in-right 0.8s ease-out 0.2s both;
}

.animate-fade-in-up {
  animation: fade-in-up 0.8s ease-out 0.2s both;
}
</style>