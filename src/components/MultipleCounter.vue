<script setup>
import { ref } from "vue";
import Counter from "./Counter.vue";
import CounterStateless from "./CounterStateless.vue";
const name2 = "Dicki 2";
const counter = ref(0);

function increment(value) {
    counter.value += value;
}
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
     <!-- v-on:click using component event -->
    <!-- <CounterStateless name="A" :counter="counter" v-on:click="() => counter += 1"></CounterStateless>
    <CounterStateless name="B" :counter="counter" v-on:click="() => counter += 2"></CounterStateless> -->

    <!-- diubah untuk component event parameter -->
    <CounterStateless name="Increment + 1" :counter="counter" :increment="1" v-on:click="increment"></CounterStateless>
    <CounterStateless name="Increment + 2" :counter="counter" :increment="2" v-on:click="increment"></CounterStateless>
    <button @click="counter++">Increment</button>
</template>
<style scoped>
</style>