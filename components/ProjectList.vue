<script setup lang="ts">
/* ───── 1. Define interface ───── */
interface Repo {
  id: number;
  name: string;
  html_url: string;
  description: string | null;
  language: string | null;
  stargazers_count: number;
}

/* ───── 2. Fetch GitHub repos (lazy load) ───── */
const {
  data: rawRepos,
  pending,
  error,
} = useLazyFetch<Repo[]>("https://api.github.com/users/siihasann/repos", {
  key: "github-repos",
  server: false, // Only fetch on client-side
});

/* ───── 3. Transform data into sorted and filtered list ───── */
const repos = computed<Repo[]>(() => {
  return (rawRepos.value ?? [])
    .filter((repo: Repo): repo is Repo => !!repo.description)
    .sort((a: Repo, b: Repo) => b.stargazers_count - a.stargazers_count);
});
</script>

<template>
  <div class="max-w-3xl mx-auto px-4">
    <p class="mb-6 text-lg text-gray-800 dark:text-gray-300">
      Here are some of the open-source projects I've built:
    </p>

    <section v-if="pending" class="text-gray-500 animate-pulse">
      Loading projects…
    </section>

    <section v-else-if="error" class="text-red-500">
      Failed to load: {{ error }}
    </section>

    <section v-else>
      <ul class="space-y-4">
        <li
          v-for="repo in repos"
          :key="repo.id"
          class="border border-gray-200 dark:border-gray-600 rounded-lg p-4 bg-white dark:bg-gray-900/10 hover:bg-gray-50 dark:hover:bg-gray-800 transition shadow-sm"
        >
          <a :href="repo.html_url" target="_blank" rel="noopener noreferrer">
            <div
              class="text-blue-600 dark:text-blue-400 font-semibold text-lg hover:underline break-words"
            >
              {{ repo.name }}
            </div>

            <p class="mt-1 text-sm text-gray-700 dark:text-gray-500">
              {{ repo.description }}
            </p>

            <div
              class="mt-3 flex items-center gap-4 text-sm text-gray-500 dark:text-gray-400"
            >
              <span v-if="repo.language" class="flex items-center gap-1">
                <svg class="w-3 h-3 fill-current" viewBox="0 0 24 24">
                  <circle cx="12" cy="12" r="10" />
                </svg>
                {{ repo.language }}
              </span>

              <span class="flex items-center gap-1">
                <svg class="w-4 h-4 fill-current" viewBox="0 0 20 20">
                  <path
                    d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.286 3.959a1 1 0 00.95.69h4.163c.969 0 1.371 1.24.588 1.81l-3.37 2.449a1 1 0 00-.364 1.118l1.287 3.96c.3.92-.755 1.688-1.54 1.117l-3.371-2.448a1 1 0 00-1.175 0l-3.371 2.448c-.785.571-1.84-.197-1.54-1.118l1.286-3.958a1 1 0 00-.364-1.118L2.314 9.386c-.783-.57-.38-1.81.588-1.81h4.163a1 1 0 00.95-.69l1.034-3.96z"
                  />
                </svg>
                {{ repo.stargazers_count }}
              </span>
            </div>
          </a>
        </li>
      </ul>
    </section>
  </div>
</template>
