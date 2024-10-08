<script setup>

const props = defineProps(["message"]);

</script>
<template>
    
    <div v-if="props.message.owner">
        <div class="message stark">
            {{ props.message.message }}
        </div>
    </div>
    <div v-else>
        <div class="message parker">
            {{ props.message.message }}
        </div>
    </div>

</template>
<style scoped>

</style>