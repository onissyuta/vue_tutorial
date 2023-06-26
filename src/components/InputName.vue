<script setup>
import { ref } from 'vue'


const name = ref("")
function onInput(e){
    name.value = e.target.value

}
</script>

<template>
    名前: <input :text="name" @input="onInput">
    <div>こんにちは、{{ name }}さん</div>
</template>

<style scoped>
    body {
        background: #fff;
    }
</style>
