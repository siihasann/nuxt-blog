<script setup>

definePageMeta({
    layout: "app",
});

const { data: blog } = await useAsyncData(() =>
    queryCollection("content").path("/blog/markdown").first()
);
</script>

<template>
    <article>
        <ContentRenderer v-if="blog" :value="blog" />
    </article>
</template>
