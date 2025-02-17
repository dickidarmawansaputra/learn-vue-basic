<script setup>
import { ref, useSlots } from 'vue';

const {title} = defineProps({
    title: String,
});

// conditional slots
const slots = useSlots(); // sebenarnya tidak perlu pake useSlots(), bisa langsung akses property yang ada di component instance

const counter = ref(0);
</script>
<template>
    <h1>{{ title }}</h1>
    <div>
        <!-- <slot/> -->
         <!-- default value slot, jika tidak diisi -->
        <!-- <slot>
            <p>Default slot</p>
        </slot> -->

        <!-- named slot -->
        <div v-if="slots.header">
            <slot name="header" :counter="counter">
                <p>Header slot</p>
            </slot>
        </div>
        <!-- akses property slots dari component instance, pake tanda $ -->
        <div v-if="$slots.content">
            <slot name="content">
                <p>Content slot</p>
            </slot>
        </div>
        <div v-if="slots.footer">
            <slot name="footer">
                <p>Footer slot</p>
            </slot>
        </div>
        <div>
            <button @click="counter++">Increment Counter</button>
        </div>
    </div>
</template>
<style scoped>
</style>