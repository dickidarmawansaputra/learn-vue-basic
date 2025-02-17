<script setup>
import { inject } from 'vue';

const profile = inject("profile");
</script>
<template>
    <h1>Profile</h1>
    <div>
        <p>Name: {{ profile.name }}</p>
        <p>Email: {{ profile.email }}</p>
    </div>
</template>
<style scoped>
</style>