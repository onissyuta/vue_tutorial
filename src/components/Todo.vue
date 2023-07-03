<script  setup>
import { ref } from 'vue'
import { computed } from 'vue';


let id = 0

const newTodo = ref('')
const hideComputed = ref(false)

const todos = ref([
    { id: id++, text: 'Learn HTML', done: false},
    { id: id++, text: 'Learn JavaScript', done: false},
    { id: id++, text: 'Learn Vue', done: false}
]);


const filteredTodos = computed(() => {
    return hideComputed.value
        ? todos.value.filter(t => !t.done)
        : todos.value
})


function addTodo(){
    todos.value.push({id: id++, text: newTodo.value, done:false});
    newTodo.value = '';
}


function removeTodo(todo){
    todos.value = todos.value.filter(t => t !== todo);
}
</script>

<template>
    <form @submit.prevent="addTodo">
        <input v-model="newTodo">
        <button>Add</button>
    </form>
    <ul>
        <li v-for="todo in filteredTodos" :key="todo.id">
            <input type="checkbox" v-model="todo.done">
            <span :class="{done: todo.done}">{{ todo.text }}</span>
            <button @click="removeTodo(todo)">X</button>
        </li>
    </ul>
    <button @click="hideComputed = !hideComputed">
        {{ hideComputed ? 'すべて表示' : '完了済みを非表示' }}
    </button>
</template>


<style scoped>
.done {
    text-decoration: line-through;
}
</style>