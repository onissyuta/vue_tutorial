<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import Form from './components/InputName.vue'
import { ref } from 'vue'

const count = ref(0)
const dynamicId = ref("title")

function increment() {
  count.value++
}


const text = ref("")
function onInput(e){
  text.value = e.target.value
}


let text_flag = ref(false)
function toggle(){
  text_flag.value = !text_flag.value
}

</script>
<!--
<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>
-->

<template>
  <p>
    <div v-bind:class="dynamicId">Red</div>
    <div :class="dynamicId">Red</div>
  </p>

  <p>
    <button v-on:click="increment">count is : {{ count }}</button>
  </p>


  <input :value="text" @input="onInput">
  <p>{{ text }}</p>



  <p>
    <button @click="toggle">切り替えボタン {{ text_flag }}</button>
    <h1 v-if="text_flag">こんにちは</h1>
  </p>

  <Form />

</template>


<style scoped>
header {
  line-height: 1.5;
}


.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}

button {

}

.title {
  color: red;
}

</style>
