<script setup>
import { ref } from 'vue';

const score = ref(70);
</script>
<template>
    <h1>Score App</h1>

    <!-- v-if jika tidak diperlukan tidak akan ditambahkan ke DOM -->
    <div v-if="score > 80">Score using v-if: A</div>
    <div v-else-if="score > 70">Score using v-if: B</div>
    <div v-else-if="score > 60">Score using v-if: C</div>
    <div v-else="score">Score using v-if: D</div>

    <hr>
    <!-- v-show semua akan ditambahkan ke DOM & menggunakan css display -->
    <div v-show="score > 80">Score using v-show: A</div>
</template>
<style scoped>
 </style>