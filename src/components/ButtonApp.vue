<script setup>
import MyButton from './MyButton.vue';

function clickHandler() {
    alert("clicked me!");
}
</script>
<template>
    <!-- semua attribute akan otomatis fallthrough attributes, syaratnya harus singgle element -->
    <!-- attribute otomatis diteruskan ke element component -->
    <MyButton class="button" @click="clickHandler" name="Dicki Darmawan Saputra" contoh="vue"></MyButton>
</template>
<style scoped>
.button {
  background-color: #04AA6D; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}
</style>