<script setup>

const props = defineProps(["chat"]);
let chat = props.chat;

function lastMessage(chatMessages) {
    if(chatMessages.length > 0) {
        return chatMessages[chatMessages.length - 1].message
    }
    else{
        return "Messages not found, start a conversation!"
    }
}

</script>
<template>

    <div class="contact">
        <div 
            class="pic"
            :style="{backgroundImage: `url(${chat.img})`}"
        >
        </div>
        <div class="badge">
            {{ chat.messages.length }}
        </div>
        <div class="name">
            {{ chat.name }}
        </div>
        <div class="message">
            {{ lastMessage(chat.messages) }}
        </div>
    </div>

</template>
<style scoped>

</style>