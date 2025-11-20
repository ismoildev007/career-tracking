<template>
  <nav class="fixed top-0 left-0 right-0 z-50 bg-white/80 backdrop-blur-xl border-b border-gray-200/50 navbar-enter">
    <div class="max-w-7xl mx-auto px-6 py-4 flex items-center justify-between">
      <!-- Logo Section -->
      <div class="flex items-center gap-2">
        <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-blue-500 via-purple-500 to-cyan-500 flex items-center justify-center">
          <Sparkles class="w-5 h-5 text-white" />
        </div>
        <span class="text-xl bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
          Career Tracking
        </span>
      </div>

      <!-- Navigation Links -->
      <div class="hidden md:flex items-center gap-8">
        <a href="#features" class="text-gray-600 hover:text-gray-900 transition-colors">
          Функции
        </a>
        <a href="#how-it-works" class="text-gray-600 hover:text-gray-900 transition-colors">
          Как работает
        </a>
        <a href="#pricing" class="text-gray-600 hover:text-gray-900 transition-colors">
          Тарифы
        </a>
        <a href="#testimonials" class="text-gray-600 hover:text-gray-900 transition-colors">
          Отзывы
        </a>
      </div>

      <!-- Action Buttons -->
      <div class="flex items-center gap-4">
        <a href="/login" class="px-6 py-2 text-gray-700 hover:text-gray-900 transition-colors">
          Войти
        </a>
        <a href="/register" class="px-6 py-2 rounded-full bg-gradient-to-r from-blue-600 to-purple-600 text-white hover:shadow-lg hover:scale-105 transition-all">
          Начать
        </a>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { Sparkles } from 'lucide-vue-next'
</script>

<style scoped>
@keyframes slideDown {
  from {
    transform: translateY(-100%);
  }
  to {
    transform: translateY(0);
  }
}

.navbar-enter {
  animation: slideDown 0.5s ease-out;
}
</style>