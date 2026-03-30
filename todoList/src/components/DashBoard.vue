<template>
    <div class="dashBorad">
        <h1 id="inputTitle">새로운 할 일 추가하기</h1>
        <inputTodo />
    </div>
</template>
    
<script setup>
import inputTodo from './inputTodo.vue';
</script>
    
<style scoped>
#inputTitle {
    color: white;
}
</style>