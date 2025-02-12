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

// gunakan parameter event untuk akses event object
// dibanding document.getElementById("eventFirstName").value
function changeFirstName(event) {
    // cara manual event modifier
    // event.preventDefault()
    person.firstName = event.target.value;
}

function changeLastName(event) {
    person.lastName = event.target.value;
}
</script>
<template>
    <div>
        <button v-on:click="increment">Increment: {{ count }}</button>
        <input type="text" id="firstName" placeholder="First Name">
        <input type="text" id="lastName" placeholder="Last Name">
        <button v-on:click="sayHello">Say Hello</button>
    </div>
    <h1>Hello, {{ fullName  }}</h1>

    <hr>
    <h1>Vue Event Handling</h1>
    <div>
        <form>
            <button @click="count++">Increment: {{ count }}</button>
            <!-- @input = v-on:input (shortcut event handler) -->
            <input type="text" id="eventFirstName" placeholder="First Name" @input="changeFirstName">
            <input type="text" id="eventLastName" placeholder="Last Name" @input="changeLastName">
            <button v-on:click.prevent="sayHello">Say Hello</button>
        </form>
    </div>
</template>
<style scoped>
</style>