<script setup>
console.info("Hello Vue")

const hello = "<b>Hello Vue</b>"
const classHello = "hello"
const id = "hello"
const buttonDisabled = true 

const data = {
    id: "hello",
    class: "hello",
}

function hi() {
    return "Hi World!";
}
</script>

<template>
<!-- dalam bentuk html escape, jika menggunakan mustache. jadi harus diperhatikan -->
<h1 class="hello">{{ hello.toUpperCase() }}</h1>

<h2>{{ 100 * 5 }}</h2>
<h2>{{ hi() }}</h2>

<!-- jika ingin raw html, bisa menggunakan directive v-html -->
<div v-html="hello"></div>

<!-- template attributes -->
<h1 :id v-bind:class="classHello">{{ hello }}</h1>
<!-- dengan shortcut -->
<h1 :class="classHello">{{ hello }}</h1>

<!-- v-bind boolean attribute -->
<button :disabled="buttonDisabled">Button disabled</button>

<!-- multiple attributes -->
 <h1 v-bind="data">{{ hello }}</h1>
 <h1 :class="data.class">{{ hello }}</h1>
</template>

<style scoped>
.hello {
    color: green;
}
</style>