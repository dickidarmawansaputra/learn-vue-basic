<script setup>
import { onWatcherCleanup, ref, watch, watchEffect } from 'vue';

const productId = ref("");
const product = ref(null);

// gunakan watch untuk mendeteksi state berubah atau tidak
// default watch => lazy
// untuk mengubahnya, menggunakan watch options immediate: true, agar langsung dieksekusi saat pertama kali 
// once: true, jika cuma ingin sekali dipanggil
watch(productId, async (newValue, oldValue) => {
    if (newValue) {
        const response = await fetch(`/${newValue}.json`);
        product.value = await response.json();
    } else {
        product.value = null
    }
});

const product2Id = ref("product1");
const product2 = ref(null);

// watch(product2Id, async (newValue, oldValue) => {
//     const response = await fetch(`/${newValue}.json`);
//     product2.value = await response.json();
// }, { immediate: true });

// watchEffect mirip dengan watch + immediate: true
watchEffect(async () => {
    // karna onWatcherCleanup tidak mendukung async, jadi harus diletakan sebelim menggunakan await 
    // ini akan di trigger ketika state berubah
    onWatcherCleanup(() => {
        console.info("cleanup");
    });

    const response = await fetch(`/${product2Id.value}.json`);
    product2.value = await response.json();
});
</script>
<template>
    <label for="productId">Product
        <select id="productId" v-model="productId">
            <option value="">Pilih</option>
            <option value="product1">Product 1</option>
            <option value="product2">Product 2</option>
            <option value="product3">Product 3</option>
        </select>
    </label>

    <div v-if="product">
        <h1>Product</h1>
        <p>ID: {{ product.id }}</p>
        <p>Name: {{ product.name }}</p>
        <p>Price: {{ product.price }}</p>
    </div>
    
    <label for="product2Id">Product With Watch Option / watchEffect
        <select id="product2Id" v-model="product2Id">
            <option value="product1">Product 1</option>
            <option value="product2">Product 2</option>
            <option value="product3">Product 3</option>
        </select>
    </label>

    <div v-if="product2">
        <h1>Product</h1>
        <p>ID: {{ product2.id }}</p>
        <p>Name: {{ product2.name }}</p>
        <p>Price: {{ product2.price }}</p>
    </div>
</template>
<style scoped></style>