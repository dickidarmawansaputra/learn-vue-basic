<script setup>
import Counter from "./Counter.vue";
</script>
<template>
    <!-- walaupun komponennya sama & dipanggil berkali-kali statenya tetap terisolasi di komponennya, -->
    <h1>Multiple Counter 1</h1>
    <Counter/>
    <h1>Multiple Counter 2</h1>
    <Counter/>
</template>
<style scoped>
</style>