<template>
    <div class="AddTodo">
        <input class="AddInput" placeholder=" New job ... " type="text" v-model="title"/>
        <button @click="AddClick" >Add</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';
let title = ref('')
const emit = defineEmits(['AddItemEvt'])
const AddClick = () => {
    if(title.value.length != 0 ){
        emit('AddItemEvt',title.value)
        title.value =''
    }
    
}
</script>

<style scoped>
.AddTodo{
    display: flex;
    justify-content: start;
    margin-top: 12px;
    
}
.AddInput{
    width: 100%;
    padding: 8px;
    font-size: 20px;
}
.AddTodo button {
    width: 30%;
    background-color: rgb(102, 210, 113);
    cursor: pointer;
}
</style>