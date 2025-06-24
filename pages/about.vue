<script setup>
definePageMeta({
    layout: 'app'
});

useHead({
    title: 'About'
});

const { data: about } = await useAsyncData(() =>
    queryCollection("content").path("/about").first()
); 

useSeoMeta({
    title: about.value?.title,
    description: about.value?.description,
})
</script>

<template>
    <article class="prose dark:prose-invert max-w-3xl mx-auto px-4 py-8">
        <ContentRenderer v-if="about" :value="about" />

    </article>
</template>