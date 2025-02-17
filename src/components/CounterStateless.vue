<script setup>
// use destructuring
// const {counter, name} = defineProps(["counter", "name"]);

// dimodifikasi agar bisa validasi untuk component event
const {counter, name, increment } = defineProps({
    counter: Number,
    name: String,
    increment: Number,
});

const emits = defineEmits(["click"]);

function buttonClick() {
    // emits("click");

    // menggunakan component event parameter
    emits("click", increment);
}
</script>
<template>
    <div>
        <h1>Counter {{ name }} : {{ counter }}</h1>
        <button @click="emits('click', increment)">Increment {{ name }}</button>
        <button @click="buttonClick">Increment {{ name }} With Func</button>
        <button @click="$emit('click', increment)">Increment {{ name }} With Component Instance</button>
    </div>
</template>
<style scoped>
</style>