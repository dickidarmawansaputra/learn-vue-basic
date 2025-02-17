<script setup>
import { ref } from 'vue';
import About from './About.vue';
import Blog from './Blog.vue';
import ContactUs from './ContactUs.vue';

const currentPage = ref("about");

const pages = {
    about: About,
    blog: Blog,
    contact: ContactUs,
}
</script>
<template>
    <button @click="currentPage = 'about'">About</button>
    <button @click="currentPage = 'blog'">Blog</button>
    <button @click="currentPage = 'contact'">Contact Us</button>
    <component :is="pages[currentPage]"></component>
</template>
<style scoped>
</style>