<script setup>
import Contact from './Contact.vue';
import { ref } from 'vue'

const props = defineProps(["chats", "callback"]);

</script>
<template>

<div class="contacts">
    
    <h2>
        Contacts
    </h2>

    <div v-for="chat in props.chats">
        <Contact
            v-bind:chat="chat"
            @click="props.callback(chat)"
            :key="chat.id"
        />
    </div>

</div>

</template>
<style scoped>

.sandwich-panel {
    padding: 5px;
    cursor: pointer;
}

</style>