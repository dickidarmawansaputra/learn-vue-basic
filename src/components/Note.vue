<script setup>
import { onBeforeMount, onBeforeUpdate, onMounted, onUpdated, reactive, ref, useTemplateRef } from 'vue';

const notes = reactive([]);
const note = ref("");
const noteInput = useTemplateRef("noteInput");
const noteList = useTemplateRef("noteList");

function addNote() {
    if (note.value) {
        notes.push(note.value);
        note.value = "";
        noteInput.value.focus();
    }
    
    // useTemplateRef dalam v-for
    if (noteList.value) {
        noteList.value.forEach((li) => {
            console.info(li.textContent);
        });
    }
}

onBeforeMount(() => {
    console.info("onBeforeMount");
});

onMounted(() => {
    console.info("onMounted");
});

onBeforeUpdate(() => {
    console.info("onBeforeUpdate");
});

onUpdated(() => {
    console.info("onUpdated");
});
</script>
<template>
    <h1>Create Note</h1>
    <div>
        <input type="text" ref="noteInput" v-model="note" placeholder="Write note here...">
        <button @click="addNote">Add Note</button>
    </div>

    <h1>List Note</h1>
    <ul>
        <!-- useTemplateRef dalam v-for -->
        <li v-for="note in notes" ref="noteList">{{ note }}</li>
    </ul>
</template>
<style scoped>
</style>