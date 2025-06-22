<script setup>

definePageMeta({
    layout: "app",
});

const { data: blog } = await useAsyncData(() =>
    queryCollection("content").path("/blog/markdown").first()
);
</script>

<template>
    <article class="prose dark:prose-invert max-w-3xl mx-auto px-4 py-8">
        <ContentRenderer v-if="blog" :value="blog" />
    </article>
</template>
