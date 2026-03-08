<template>
    <header class="flex flex-row items-center gap-4 px-8 py-4 fixed top-0 left-0 w-full bg-white/60 backdrop-blur-md z-50">
        <NuxtLink
            class="text-xl"
            to="/"
        >海城中高物理部</NuxtLink>
        <div class="grow"/>
        <div class="sm:flex flex-row items-center gap-4 hidden">
            <NuxtLink to="/works">Works</NuxtLink>
            <NuxtLink to="/blogs">Blogs</NuxtLink>
            <NuxtLink to="https://www.youtube.com/@kaijo_physics">YouTube</NuxtLink>
            <NuxtLink to="https://twitter.com/kaijo_physics">𝕏</NuxtLink>
            <NuxtLink to="https://www.instagram.com/kaijo_physics/">Instagram</NuxtLink>
        </div>
        <button
            class="sm:hidden"
            @click="showNavBar = !showNavBar">
            <Icon name="clarity:menu-line" color="black" size="24"/>
        </button>
    </header>
    <div
        v-if="showNavBar"
        class="fixed left-0 top-0 p-8 h-screen w-screen text-lg bg-white shadow-md flex flex-col gap-4 items-center transition-all duration-300">
        <button
            class="sm:hidden"
            @click="showNavBar = !showNavBar">
            <Icon name="iconamoon:close-thin" color="black" size="24"/>
        </button>
        <NuxtLink to="/works">Works</NuxtLink>
        <NuxtLink to="/blogs">Blogs</NuxtLink>
        <NuxtLink to="https://www.youtube.com/@user-qm9fz9tl4w">Youtube</NuxtLink>
        <NuxtLink to="https://twitter.com/kaijo_physics">𝕏</NuxtLink>
        <NuxtLink to="https://www.instagram.com/kaijo_physics/">Instagram</NuxtLink>
    </div>
</template>
<script setup lang="ts">
const showNavBar = ref(false)
</script>
