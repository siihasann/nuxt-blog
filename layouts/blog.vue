<template>
    <div class="container">
        <div class="col-left">
            <nav>
                <ul>
                    <li><NuxtLink to="/">Home</NuxtLink></li>
                    <li><NuxtLink to="/about">About</NuxtLink></li>
                    <li><NuxtLink to="/blog">Blog</NuxtLink></li>
                    <li><NuxtLink to="/project">Project</NuxtLink></li>
                </ul>
            </nav>
        </div>
        <div class="col-right">
            <slot/>
        </div>
    </div>
</template>

<style scoped>
    .container {
        display: grid;
        grid-template-columns: 1fr 3fr;
        height: 100vh;
    }

    .col-left {
        background-color: lightblue;
        padding: 20px;
    }

    .col-right {
        padding: 20px;
        background-color: lightgreen;
    }
</style>