<script setup>
useHead({
    titleTemplate: '%s - Sans Porto',
    link: [
        {
            rel: 'preconnect',
            href: 'https://fonts.googleapis.com',
        },
        {
            rel: 'stylesheet',
            href: 'https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap" rel="stylesheet',
            crossorigin: 'anonymous',
        },
    ],
});

useSeoMeta({
    title: 'My Amazing Site',
    ogTitle: 'My Amazing Site',
    description: 'This is my amazing site, let me tell you all about it.',
    ogDescription: 'This is my amazing site, let me tell you all about it.',
    ogImage: 'https://example.com/image.png',
    twitterCard: 'summary_large_image',
    twitterTitle: 'My Amazing Site',
    twitterDescription: 'This is my amazing site, let me tell you all about it.',
});
</script>

<template>
    <div class="container mx-auto">
        <Header/>

        <main class="p-4">
            <slot/>
        </main>
    </div>
</template>

<style>
body {
    font-family: 'Poppins', sans-serif;
}
</style>