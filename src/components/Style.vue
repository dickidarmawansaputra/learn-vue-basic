<script setup>
import { ref } from 'vue';

const styles = ["red", "bold"];

const red = ref(false);
const bold = ref(false);

function toggleRed() {
    red.value = !red.value;
}

function toggleBold() {
    bold.value = !bold.value;
}

const inlineStyleColor = {
    color: "red",
}

// karena di js tidak bisa seperti kode css, jadi di css: text-transform => textTransform
const inlineStyleText ={
    textTransform: "uppercase",
    fontWeight: "bold",
}
</script>
<template>
    <!-- red:red = class red di style : red ref -->
    <h1 v-bind:class="{red:red, bold:bold }">Style</h1>
    <h1 v-bind:class="styles">Style</h1>

    <h1 v-bind:style="inlineStyleColor">Inline Style</h1>
    <h1 v-bind:style="inlineStyleText ">Inline Style</h1>
    <h1 v-bind:style="[inlineStyleColor, inlineStyleText] ">Inline Style</h1>
    <button v-on:click="toggleRed">Red</button>
    <button v-on:click="toggleBold">Bold</button>
</template>
<style scoped>
.red {
    color: red;
}

.bold {
    text-transform: uppercase;
    font-weight: bold;
}
</style>