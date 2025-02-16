<script setup>
import Container from './Container.vue';
import MyButton from './MyButton.vue';

function clickHandler() {
    alert("clicked me!");
}
</script>
<template>
    <!-- semua attribute akan otomatis fallthrough attributes, syaratnya harus singgle element -->
    <!-- attribute otomatis diteruskan ke element component -->
    <!-- <MyButton class="button" @click="clickHandler" name="Dicki Darmawan Saputra" contoh="vue"></MyButton> -->

    <!-- Component slot -->
    <!-- <Container title="Contoh button">
      <MyButton class="button" @click="clickHandler" name="Dicki Darmawan Saputra" contoh="vue"></MyButton>
    </Container> -->
    
    <!-- named slot -->
    <Container title="Contoh button">
      <template v-slot:header="attributes">
        <h1>Ini header {{ attributes.counter }}</h1>
      </template>
      <!-- shortcut v-slot:content -->
      <template #content>
        <p>Ini Content</p>
      </template>
      <template v-slot:footer>
        <h4>Ini footer</h4>
      </template>
    </Container>
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