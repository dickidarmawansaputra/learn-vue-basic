<script setup>
import { reactive } from 'vue';
import ContactForm from './ContactForm.vue';
import ContactList from './ContactList.vue';

const contact = reactive({
    name: "",
    email: "",
    age: 0,
    type: "Regular",
    complain: false,
    message: "",
});


</script>
<template>
    <h1>Contact Us</h1>
    <ContactForm v-model="contact" />
    <!-- diganti pake model, ini untuk pembelajaran saja. Namun tidak ideal -->
     <ContactList 
        v-model:name.uppercase="contact.name"
        v-model:email="contact.email"
        v-model:age="contact.age"
        v-model:type="contact.type"
        v-model:complain="contact.complain"
        v-model:message="contact.message"
    />

    <!-- sebelum menggunakan component model -->
    <!-- <form>
        <div>
            <label for="name">Name
                <input type="text" id="name" v-model="contact.name">
            </label>
        </div>
        <div>
            <label for="email">Email
                <input type="email" id="email" v-model="contact.email">
            </label>
        </div>
        <div>
            <label for="age">Age
                <input type="number" id="age" v-model.number="contact.age">
            </label>
        </div>
        <div>
            <label for="type">Type
                <select id="type" v-model="contact.type">
                    <option value="Regular">Regular</option>
                    <option value="VIP">VIP</option>
                </select>
            </label>
        </div>
        <div>
            <label for="complain">Complain
                <input type="checkbox" id="complain" v-model="contact.complain">
            </label>
        </div>
        <div>
            <label for="message">Message
                <textarea name="message" id="message" v-model="contact.message"></textarea>
            </label>
        </div>
    </form> -->

    <!-- <h1>Preview</h1>
    <div>
        <p>Name: {{ contact.name }}</p>
        <p>Email: {{ contact.email }}</p>
        <p>Age: {{ contact.age }}</p>
        <p>Type: {{ contact.type }}</p>
        <p>Complain: {{ contact.complain }}</p>
        <p>Message: {{ contact.message }}</p>
    </div> -->
</template>
<style scoped></style>