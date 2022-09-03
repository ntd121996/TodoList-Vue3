<template>
    
    <AddTodoItem @add-item-evt="AddItem"/>
    <div>
        <TodoListItem v-for="todo in todos" :key="todo.id" :Item ="todo" @delete-evt="DeleteClicked"/>
    </div>
</template>

<script setup>
import {ref} from 'vue'
import TodoListItem from './TodoListItem.vue'
import AddTodoItem from './AddTodoItem.vue'
let todos = ref([
        {
            id: 0,
            title:"Job1",
            completed: false,
        },
        {
            id: 1,
            title:"Job2",
            completed: false,
        },
        {
            id: 2,
            title:"Job3",
            completed: false,
        },
    ])
const DeleteClicked = (id) => {
    todos.value = todos.value.filter(todo => todo.id !== id)
}
const AddItem = (title) => {
    const id = todos.value.length
    const newItem = {
        id,
        title,
        completed:false,
    }
    todos.value.push(newItem);
}
</script>


<style scoped>

</style>