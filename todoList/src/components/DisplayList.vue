<template>
    <div class="displayList">
        <inputTodo @input-list="saveTodo"/>
        <div v-for="item in list1" class="todoBox">
            <input type="checkbox" name="item" class="todo input" v-model="item.completed">
            <label for="item"> {{ item.todo }} </label>
            <span class="deleteBtn" @click="deleteTodo(item)">삭제</span>
        </div>
    </div>
</template>
    
<script setup>
import inputTodo from './inputTodo.vue';
import { ref } from 'vue';

const list1 = ref([]);

const saveTodo = ((item) => {
    list1.value = item;
})

function deleteTodo(item) {
    list1.value.splice(item, 1);
}

</script>
    
<style scoped>
    .todo {
    width: 550px;
    height: 80px;
    background: white;
    margin: 20px;
    
}

.todo {
    width: 20px;
    height: 20px;
    background-color: white;
}

.todoBox {
    width: 300px;
    height: 50px;
    background: skyblue;
    margin-bottom: 20px;
    border: solid 1px navy;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.deleteBtn {
    cursor: pointer;
}
</style>