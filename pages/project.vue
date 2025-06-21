<script setup>
definePageMeta({
    layout: 'app'
});

useHead({
    title: 'Project'
});

const { error, pending, data } = await useFetch('https://api.github.com/users/siihasann/repos');
</script>


<template>
    Project Page
    <section v-if="pending">Load..</section>
    <section v-else-if="error">Someting went wrong..</section>
    <section v-else>{{ data }}</section>
</template>