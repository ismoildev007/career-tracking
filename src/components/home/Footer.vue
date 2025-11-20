<script setup>
import { Sparkles, Twitter, Linkedin, Instagram, Facebook } from "lucide-vue-next";
</script>

<template>
  <footer class="bg-gray-900 text-gray-300">
    <div class="max-w-7xl mx-auto px-6 py-16">
      <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-12 mb-12">

        <!-- Brand -->
        <div class="lg:col-span-2">
          <div class="flex items-center gap-2 mb-4">
            <div
                class="w-10 h-10 rounded-xl bg-gradient-to-br from-blue-500 via-purple-500 to-cyan-500 flex items-center justify-center"
            >
              <Sparkles class="w-5 h-5 text-white" />
            </div>
            <span class="text-xl text-white">Career Tracking</span>
          </div>

          <p class="text-gray-400 max-w-md mb-6">
            Персональная платформа для карьерного роста с использованием искусственного интеллекта.
            Развивайтесь системно, отслеживайте прогресс и достигайте новых высот.
          </p>

          <div class="flex gap-4">
            <a
                href="#"
                class="w-10 h-10 rounded-xl bg-gray-800 hover:bg-gradient-to-br hover:from-blue-500 hover:to-purple-500 flex items-center justify-center transition-all"
            >
              <Twitter class="w-5 h-5" />
            </a>

            <a
                href="#"
                class="w-10 h-10 rounded-xl bg-gray-800 hover:bg-gradient-to-br hover:from-blue-500 hover:to-purple-500 flex items-center justify-center transition-all"
            >
              <Linkedin class="w-5 h-5" />
            </a>

            <a
                href="#"
                class="w-10 h-10 rounded-xl bg-gray-800 hover:bg-gradient-to-br hover:from-blue-500 hover:to-purple-500 flex items-center justify-center transition-all"
            >
              <Instagram class="w-5 h-5" />
            </a>

            <a
                href="#"
                class="w-10 h-10 rounded-xl bg-gray-800 hover:bg-gradient-to-br hover:from-blue-500 hover:to-purple-500 flex items-center justify-center transition-all"
            >
              <Facebook class="w-5 h-5" />
            </a>
          </div>
        </div>

        <!-- Platform -->
        <div>
          <h3 class="text-white mb-4">Платформа</h3>
          <ul class="space-y-3">
            <li><a href="#" class="hover:text-white transition-colors">Функции</a></li>
            <li><a href="#" class="hover:text-white transition-colors">Как работает</a></li>
            <li><a href="#" class="hover:text-white transition-colors">Тарифы</a></li>
            <li><a href="#" class="hover:text-white transition-colors">Отзывы</a></li>
            <li><a href="#" class="hover:text-white transition-colors">Блог</a></li>
          </ul>
        </div>

        <!-- Company -->
        <div>
          <h3 class="text-white mb-4">Компания</h3>
          <ul class="space-y-3">
            <li><a href="#" class="hover:text-white transition-colors">О нас</a></li>
            <li><a href="#" class="hover:text-white transition-colors">Поддержка</a></li>
            <li><a href="#" class="hover:text-white transition-colors">Контакты</a></li>
            <li><a href="#" class="hover:text-white transition-colors">Политика конфиденциальности</a></li>
            <li><a href="#" class="hover:text-white transition-colors">Условия использования</a></li>
          </ul>
        </div>
      </div>

      <!-- Bottom -->
      <div class="pt-8 border-t border-gray-800 flex flex-col md:flex-row justify-between items-center gap-4">
        <p class="text-gray-500 text-sm">
          © 2025 Career Tracking. Все права защищены.
        </p>

        <div class="flex gap-6 text-sm">
          <a href="#" class="hover:text-white transition-colors">Политика конфиденциальности</a>
          <a href="#" class="hover:text-white transition-colors">Условия использования</a>
          <a href="#" class="hover:text-white transition-colors">Cookie</a>
        </div>
      </div>
    </div>
  </footer>
</template>
