<script setup lang="ts">
import { ClientOnly } from '#components';

const navigation = [
  { name: 'Home', href: '/' },
  { name: 'Projects', href: '/project' },
  { name: 'About', href: '/about' },
//   { name: 'Contact', href: '/contact' }
]
</script>

<template>
  <header class="sticky top-0 z-50 bg-white/80 dark:bg-gray-900/80 backdrop-blur-md border-b border-gray-200 dark:border-gray-700">
    <nav class="container mx-auto px-4 py-4">
      <div class="flex items-center justify-between">
        <div class="flex items-center space-x-4">
          <NuxtLink
            to="/"
            class="text-xl font-bold text-gray-900 dark:text-white hover:text-blue-600 dark:hover:text-blue-400 transition-colors"
          >
            Sans Porto
          </NuxtLink>
        </div>

        <div class="hidden md:flex items-center space-x-8">
          <nav class="flex space-x-6">
            <NuxtLink
              v-for="item in navigation"
              :key="item.name"
              :to="item.href"
              class="text-gray-700 dark:text-gray-300 hover:text-blue-600 dark:hover:text-blue-400 transition-colors font-medium"
              active-class="text-blue-600 dark:text-blue-400"
            >
              {{ item.name }}
            </NuxtLink>
          </nav>
          <ClientOnly>
            <ThemeToggle />
          </ClientOnly>
        </div>

        <div class="flex md:hidden items-center space-x-2">
                <ThemeToggle />
          <button
            class="p-2 rounded-lg bg-gray-100 dark:bg-gray-800 hover:bg-gray-200 dark:hover:bg-gray-700 transition-colors"
            aria-label="Toggle mobile menu"
          >
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            </svg>
          </button>
        </div>
      </div>
    </nav>
  </header>
</template>