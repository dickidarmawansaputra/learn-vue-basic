<script setup>
import { reactive } from 'vue';

// reactive hanya untuk tipe data object, array, colllection (bukan tipe data primitive)
// cocok untuk kompleks object, tp jika manipulasi yang lebih di kompleks object bisa gunakan kembali ref
const person = reactive({
    firstName: "",
    lastName: "",
})

function sayHello() {
    person.firstName = document.getElementById("firstName").value;
    person.lastName = document.getElementById("lastName").value;
}
</script>
<template>
    <div>
        <input type="text" id="firstName" placeholder="First Name">
        <input type="text" id="lastName" placeholder="Last Name">
        <button v-on:click="sayHello">Say Hello</button>
    </div>
    <h1>Hello, {{ person.firstName }} {{ person.lastName }}</h1>
</template>
<style scoped>
</style>