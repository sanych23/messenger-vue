<script setup>
import Message from './Message.vue';
import SandwichPanel from '../UI/SandwichPanel.vue';
import Typing from './Typing.vue';
import throttle from 'lodash.throttle';
import { onUpdated, ref } from 'vue';

const props = defineProps(["chat_data", "callback"]);
const messages = ref(props.chat_data);

function scrollToBottom() {
    if(chat){
        chat.scrollTop = chat.scrollHeight;
    }
};


let typingStatus = ref(false);

const throttledMethod = throttle(() => {
    typingStatus.value = false;
}, 4000);

function addMsg(evt){
    if(evt.code == "Enter"){
        props.chat_data.messages.push({
            message: evt.target.value,
            owner: null,
            time: "11:41",
        });
        evt.target.value = "";
    }
    scrollToBottom();
}

onUpdated(() => {
   scrollToBottom(); 
   console.log("must be scrolled");
});

</script>
<template>


<div class="chat" v-if="props.chat_data">
    <div class="contact bar inline-head-message">
        <div class="chat-info">
            <div 
                class="chat-avatar"
                :style="{backgroundImage: `url(${props.chat_data.img})`}"  
            >
            </div>
            <div>
                <div class="name">
                    {{ props.chat_data.name }}
                </div>
                <div class="seen">
                    Today at 12:56
                </div>
            </div>
        </div>
        <SandwichPanel 
            :style="{marginLeft: 'auto'}"
            @click="props.callback"
        />
    </div>
    <div class="messages" id="chat" ref="chat">
        <div class="time">
            Today at 11:41
        </div>

        <div v-for="message in props.chat_data.messages">
            <Message v-bind:message="message"/>  
        </div>


        <Typing 
            v-bind:status="typingStatus"
            v-if="typingStatus"
        /> 
    
    </div>
    
    <div class="input">
        <font-awesome-icon :icon="['fas', 'camera']" class="size-sticker"/>
        <font-awesome-icon :icon="['fas', 'face-laugh-beam']" class="size-sticker" style="margin-left: 1rem; margin-right: 1rem;"/>
        <input 
            placeholder="Type your message here!" 
            type="text"
            v-on:keyup.enter="addMsg"
            @keyup="throttledMethod"
            @keydown="typingStatus=true"
        />
        <font-awesome-icon :icon="['fas', 'microphone']" class="size-sticker"/>
    </div>

</div>

<div class="chat" v-else>
    <div class="contact bar inline-head-message">
        <div class="name">
             Select Chat 
        </div>
        <SandwichPanel 
            class="sandwich-panel"
            @click="props.callback"    
        />
    </div>
    <div class="messages" id="chat">
        <h3 style="text-align: center;">Unknown Chat</h3>
    </div>
    <div class="input">
    </div>
</div>

</template>
<style scoped>
    .typing-active{
        display: block;
    }
    .size-sticker{
        font-size: 1.5rem;
    }
    .inline-head-message{
        align-items: center;
        justify-content: center;
        padding: 0px;
        flex-direction: row;
    }
    .sandwich-panel{
        margin-left: auto;
    }
    .chat-avatar{
        width: 4rem;
        height: 4rem;
        background-size: cover;
        background-position: center;
        border-radius: 50%;
    }
    .chat-info{
        display: flex;
        align-items: center;
        gap: 1rem;
    }
</style>