<script setup>
import { computed, reactive, ref } from 'vue';

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

// tanpa computed properties
// function fullName() {
//     console.info("fullname called");
//     return `${person.firstName} ${person.lastName}`;
// }

const count = ref(0);

function increment() {
    console.info("increment called");
    count.value++;
}

// untuk melihat value sebelumnya bisa ditambahkan di parameter
const fullName = computed((oldName) => {
    console.info("fullname called");
    console.info(`old name value: ${oldName}`);
    return `${person.firstName} ${person.lastName}`;
});
</script>
<template>
    <div>
        <button v-on:click="increment">Increment: {{ count }}</button>
        <input type="text" id="firstName" placeholder="First Name">
        <input type="text" id="lastName" placeholder="Last Name">
        <button v-on:click="sayHello">Say Hello</button>
    </div>
    <h1>Hello, {{ fullName  }}</h1>
</template>
<style scoped>
</style>