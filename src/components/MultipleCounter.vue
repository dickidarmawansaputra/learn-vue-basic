<script setup>
import { ref } from "vue";
import Counter from "./Counter.vue";
import CounterStateless from "./CounterStateless.vue";
const name2 = "Dicki 2";
const counter = ref(0);
</script>
<template>
    <!-- walaupun komponennya sama & dipanggil berkali-kali statenya tetap terisolasi di komponennya, -->
    <h1>Multiple Counter 1</h1>
    <Counter name="Dicki Darmawan Saputra" initial-count="10"/>
    <h1>Multiple Counter 2</h1>
    <Counter v-bind:name="name2" initial-count="20"/>
    <br>
    <h1>Counter Stateless</h1>
    <!-- Semua props One-Way Data Flow  dari parent ke child component-->
    <!-- sharing state bikin di parent & kirimkan state ke child -->
    <CounterStateless name="A" :counter="counter"></CounterStateless>
    <CounterStateless name="B" :counter="counter"></CounterStateless>
    <button @click="counter++">Increment</button>
</template>
<style scoped>
</style>