<template>
    <header class="flex justify-between items-center mt-5">
    <div>
        <NuxtLink to="/" class="text-xl font-semibold p-2 hover:bg-gray-200">Porto</NuxtLink>
    </div>
        <nav class="font-mono">
            <ul class="flex space-x-4">
            <li><NuxtLink to="/" class="p-2 hover:bg-gray-200">Home</NuxtLink></li>
            <li><NuxtLink to="/about" class="p-2 hover:bg-gray-200">About</NuxtLink></li>
            <li><NuxtLink to="/blog" class="p-2 hover:bg-gray-200">Blog</NuxtLink></li>
            <li><NuxtLink to="/project" class="p-2 hover:bg-gray-200">Project</NuxtLink></li>
            </ul>
        </nav>
    </header>
</template>
