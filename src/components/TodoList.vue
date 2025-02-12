<script setup>
const items = [
    {
        id: 1,
        text: "A",
        done: true,
    },
    {
        id: 2,
        text: "B",
        done: false,
    },
    {
        id: 3,
        text: "C",
        done: true,
    },
    {
        id: 4,
        text: "D",
        done: false,
    },
    {
        id: 5,
        text: "E",
        done: false,
    },
];
</script>
<template>
    <h1>Todolist APP</h1>
    <ul>
        <li v-for="item in items">
            {{ item.text }}
        </li>
    </ul>

    <h1>List For Object</h1>
    <ul v-for="item in items">
        <li v-for="(value, key) in item">
            {{ key }}: {{ value }}
        </li>
    </ul>
    
    <h1>List For Range</h1>
    <ul>
        <li v-for="i in 10">
            {{ i }}
        </li>
    </ul>

    <!-- untuk mempercepat dan mencegah vue mereplace ulang seluruh element setiap kali rendering -->
    <h1>Binding Key</h1>
    <ul v-for="item in items" v-bind:key="item.id">
        <li v-for="(value, key) in item" v-bind:key="key">
            {{ key }}: {{ value }}
        </li>
    </ul>
    
    <h1>PENGGABUNGAN V-FOR & V-IF DALAM 1 ELEMENT (PRIORITAS UTAMA V-IF DIBANDING V-FOR)</h1>
    <!-- contoh salah -->
    <!-- <ul v-for="item in items" v-bind:key="item.id" v-if="!item.done">
        <li v-for="(value, key) in item" v-bind:key="key">
            {{ key }}: {{ value }}
        </li>
    </ul> -->

    <!-- contoh benar -->
    <template v-for="item in items">
        <ul v-if="!item.done" v-bind:key="item.id">
            <li v-for="(value, key) in item" v-bind:key="key">
                {{ key }}: {{ value }}
            </li>
        </ul>
    </template>
</template>
<style scoped>
 </style>