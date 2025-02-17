<script setup>
import { provide, reactive } from 'vue';
import ProfileAddress from './ProfileAddress.vue';
import Profile from './Profile.vue';

const profile = reactive({
    name: "Dicki Darmawan Saputra",
    email: "dicki@mail.com",
});

// sebisa mungkin menggunakan ini jika sudah sulit menggunakan props
// contoh case yg cocok: setelah login simpan data profile, agar semua komponen bisa dapat data profile bisa pake provide & inject
provide("profile", profile);
</script>
<template>
    <input type="text" v-model="profile.name" placeholder="Name">
    <Profile></Profile> 
    <ProfileAddress></ProfileAddress>
</template>
<style scoped>
 </style> 