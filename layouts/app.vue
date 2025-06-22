<script setup lang="ts">
useSeoMeta({
  title: 'Sans Porto',
  titleTemplate: '%s - Sans Porto',
  description: 'Portfolio website showcasing my projects and skills',
  ogTitle: 'Sans Porto - Developer Portfolio',
  ogDescription: 'Portfolio website showcasing my projects and skills',
  ogImage: '/og-image.png',
  ogUrl: 'https://your-domain.com',
  twitterCard: 'summary_large_image',
  twitterTitle: 'Sans Porto - Developer Portfolio',
  twitterDescription: 'Portfolio website showcasing my projects and skills',
  twitterImage: '/og-image.png'
})

useHead({
  htmlAttrs: {
    lang: 'en'
  },
  meta: [
    { name: 'theme-color', content: '#ffffff' },
    { name: 'theme-color', content: '#111827', media: '(prefers-color-scheme: dark)' }
  ]
})
</script>

<template>
  <div class="min-h-screen bg-white dark:bg-gray-900 transition-colors duration-300">
    <Header />

    <main class="container mx-auto px-4 py-8">
      <slot />
    </main>

    <footer class="mt-auto py-6 border-t border-gray-200 dark:border-gray-700">
      <div class="container mx-auto px-4 text-center text-gray-600 dark:text-gray-400">
        <p>&copy; 2025 Sans Porto. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>