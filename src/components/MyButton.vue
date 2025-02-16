<script setup>
import { useAttrs } from 'vue';

// untuk menonaktifkan Fallthrough Attributes
defineOptions({
    inheritAttrs: false,
})

// kalo defineProps() maka contoh akan masuk di props, jika tanpa props maka otomatis masuk ke useAttrs()
// const props = defineProps(["contoh"]);
// console.info(props);

// cuma disarankan tetap didefinisikan pake props
const attributes = useAttrs();
 console.info(attributes);
</script>
<template>
    <button>My Button: {{ attributes.name }}</button>
</template>
<style scoped>
</style>