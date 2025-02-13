<script setup>
import { nextTick, ref } from 'vue';

// cara panggilnya cek di file MultipleCounter.vue
const props = defineProps(["name", "initialCount"]);

console.info("load component")
// using reactive state
let count = ref(0);

function increment() {
    count.value++;
    console.info(`Counter: ${count.value}`)

    // sebelum pake reative state, update DOM manual
    // document.getElementById("count").innerText = `Counter: ${count}`;
}

// ref bisa nerima semua tipe data
let countObject = ref({
    // sebelum gunakan props, yg dibawah untuk mencoba component props
    // count: 0,
    count: Number(props.initialCount),
    name: "Dicki",
});

function incrementObject() {
    countObject.value.count++;
    console.info(`Counter Object: ${countObject.value.count}`)
}

async function incrementObjectWithAsync() {
    countObject.value.count++;
    console.info("increment count before next tick");
    console.info(`Counter Object: ${countObject.value.count}`)

    countObject.value.count++;
    countObject.value.count++;
    countObject.value.count++;

    // pejadwalan vue render ulang (tunggu render ulang)
    await nextTick();
    console.info("increment count after next tick");
}
</script>

<template>
    <div>
        <h1>Counter: {{ count }}</h1>
        <h1>Counter Object: {{ countObject.count }}</h1>
        <h1>Counter Props {{ props.name }} : {{ countObject.count }}</h1>
        <button v-on:click="increment">Increment</button>
        <button v-on:click="incrementObject">Increment Object</button>
        <button v-on:click="incrementObjectWithAsync">Increment Object With Async</button>

    </div>
</template>

<style scoped>
</style>