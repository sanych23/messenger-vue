<script setup>
import { ref } from 'vue'
import Chat from './components/Chat.vue';

let data = ref({
  chats: [
    {
      id: 1,
      name: 'Steve Rogers',
      img: 'https://vignette.wikia.nocookie.net/marvelcinematicuniverse/images/7/7c/Cap.America_%28We_Don%27t_Trade_Lives_Vision%29.png',
      messages: [],
    },
    {
      id: 2,
      name: 'Tony Stark',
      img: 'https://vignette.wikia.nocookie.net/marvelcinematicuniverse/images/7/73/SMH_Mentor_6.png',
      messages: [
        {
          time: '10:00',
          message: 'Hey man! Whats up, Mr. Stark?',
          owner: null,
        },
        {
          time: '10:01',
          message: 'Kid whered you come from?',
          owner: "Tony Stark"
        },
        {
          time: '10:02',
          message: 'Field trip',
          owner: null
        },
        {
          time: '10:03',
          message: 'Uh, What is this guys problem, Mr.Stark?',
          owner: null
        },
        {
          time: '10:04',
          message: 'Uh, hes from space, he came here to steal a necklace from a wizard.',
          owner: 'Tony Stark'
        }
      ]
    },
    {
      id: 3,
      name: 'Bruce Banner',
      img: 'https://vignette.wikia.nocookie.net/marvelcinematicuniverse/images/4/4f/BruceHulk-Endgame-TravelingCapInPast.jpg',
      messages: [
      {
          time: '10:03',
          message: 'Hi',
          owner: 'Tony Stark'
        },
        {
          time: '10:04',
          message: 'Hi, how are you?',
          owner: null
        }
      ]
    },
    {
      id: 4,
      name: 'Thor Odinson',
      img: 'https://vignette.wikia.nocookie.net/marvelcinematicuniverse/images/9/98/ThorFliesThroughTheAnus.jpg',
      messages: []
    }
  ]
});

</script>

<template>
  
  <Chat v-bind:data="data">
  </Chat>
  
</template>

<style>
  @import url('https://fonts.googleapis.com/css?family=Red+Hat+Display:400,500,900&display=swap');
</style>
