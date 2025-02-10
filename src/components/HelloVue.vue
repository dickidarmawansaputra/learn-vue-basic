<script setup>
console.info("Hello Vue")

const hello = "<b>Hello Vue</b>"
</script>

<template>
<!-- dalam bentuk html escape, jika menggunakan mustache. jadi harus diperhatikan -->
<h1 class="hello">{{ hello }}</h1>

<!-- jika ingin raw html, bisa menggunakan directive v-html -->
<div v-html="hello"></div>
</template>

<style scoped>
.hello {
    color: green;
}
</style>