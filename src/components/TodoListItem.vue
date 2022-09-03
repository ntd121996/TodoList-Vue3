<template>
    <div class="todoItem">
        <div :class= "['item', Item.completed ? 'completed' : '']">
            <input type="checkbox" class="checkboxItem" :checked="Item.completed" @change="markItemCompleted"/>
            <p> {{Item.title}}</p>
        </div>
        <button class="btn-del " @click="DeleteClicked"> Delete</button>
    </div>
</template>

<script setup>
const prop = defineProps({ Item: Object})
const emit = defineEmits(['DeleteEvt'])
const markItemCompleted = () =>{
    prop.Item.completed = !prop.Item.completed;
}
const DeleteClicked = () =>{
    emit('DeleteEvt',  prop.Item.id)

}
</script>

<style scoped>
    .todoItem{
        display: flex;
        justify-content: center;
        color: #000;
        border-bottom: 1px #ccc;
        font-size: 30px;
        margin-top: 24px;
    }
    .item {
        display: flex;
        width: 80%;
        justify-content: flex-start;
        flex-wrap: wrap;
    }
    p {
        padding: 8px 24px;
        margin: auto 0;
        width: 50%;
        word-break: break-all;
        
        
    }
    .checkboxItem {
        width: 18px;
        cursor: pointer;
    }
    .btn-del{
        background-color: red;
        cursor: pointer;
        color:#fff;
        height: 44px;
    }
    .completed {
        text-decoration: line-through;
    }
    .text-decoration-none {
    }

</style>