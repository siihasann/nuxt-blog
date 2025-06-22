<script setup lang="ts">
interface Repo {
  id: number
  name: string
  html_url: string
  description: string | null
  language: string | null
  stargazers_count: number
}

const { data: repos, pending, error } = useFetch<Repo[]>(
  'https://api.github.com/users/siihasann/repos',
  { key: 'github-repos' }
)
</script>

<template>
  <div class="max-w-3xl mx-auto px-4">
    <p class="mb-6 text-lg text-gray-800 dark:text-gray-300">
      Here are some of the open-source projects I've built:
    </p>

    <!-- Loading State -->
    <section v-if="pending" class="animate-pulse text-gray-500">
      Loading projects…
    </section>

    <!-- Error State -->
    <section v-else-if="error" class="text-red-500">
      Something went wrong: {{ error.message ?? error }}
    </section>

    <!-- Success State -->
    <section v-else>
      <ul class="space-y-4">
        <li
          v-for="repo in repos"
          :key="repo.id"
          class="border border-gray-200 dark:border-gray-500 rounded-lg p-4 bg-white dark:bg-gray-900/10 hover:bg-gray-50 dark:hover:bg-gray-800 shadow-xs shadow-gray-400 transition"
        >
          <!-- Repo Name -->
          <a
            :href="repo.html_url"
            target="_blank"
            class="block font-semibold text-blue-600 dark:text-blue-400 text-lg hover:underline break-words"
          >
            {{ repo.name }}
          </a>

          <!-- Description -->
          <p class="text-sm text-gray-700 dark:text-gray-300 mt-1">
            {{ repo.description || 'No description provided.' }}
          </p>

          <!-- Language and Stars -->
          <div class="flex items-center gap-4 text-sm text-gray-500 dark:text-gray-400 mt-3">
            <span v-if="repo.language" class="flex items-center gap-1">
              <svg class="w-3 h-3 fill-current" viewBox="0 0 24 24">
                <circle cx="12" cy="12" r="10" />
              </svg>
              {{ repo.language }}
            </span>

            <span class="flex items-center gap-1">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="currentColor" viewBox="0 0 20 20">
                <path
                  d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.286 3.959a1
                1 0 00.95.69h4.163c.969 0 1.371 1.24.588
                1.81l-3.37 2.449a1 1 0
                00-.364 1.118l1.287
                3.96c.3.92-.755
                1.688-1.54
                1.117l-3.371-2.448a1
                1 0 00-1.175
                0l-3.371
                2.448c-.785.571-1.84-.197-1.54-1.118l1.286-3.958a1
                1 0 00-.364-1.118L2.314
                9.386c-.783-.57-.38-1.81.588-1.81h4.163a1
                1 0 00.95-.69l1.034-3.96z"
                />
              </svg>
              {{ repo.stargazers_count }}
            </span>
          </div>
        </li>
      </ul>
    </section>
  </div>
</template>
