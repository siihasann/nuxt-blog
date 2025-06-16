<script setup>
const route = useRoute();
// console.log(route);
</script>


<template>
    <h1>Blog Page</h1>
    <p>this is {{ route.params.slug }} the blog page.</p>
</template>