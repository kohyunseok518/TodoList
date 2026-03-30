<!-- 
컴포넌트 구조 변경
컴포넌트가 마운트 될 때 저장된 정보 있으면 데리고 올리기
1. todo 입력 받고 -> 스트링으로 변환헤서 저장 
2.  객체가 있으면 변환해서 배열에 넣기
3. 컴포넌트가 마운트 될 때 로컬스토리지에 데이터가 있으면 태우기
4. 객체로 변환해서 다시 배열에 꽂기


-> emit할 데이터 todo만 emit하고 돌리면 됨
[{...}, {...}, {...}] -> 문자열
객체 변환 [{...}, {...}, {...}] 
-->

<!-- 
구조 수정
-->

<template> 
<div>
    <input type="text" id="inputTodo" v-model="msg">
    <button id="inputBtn" @click="addTodo">추가하기</button>
</div>
</template>
    
<script setup>
import {ref, defineEmits, onMounted} from 'vue';

    const msg = ref('');
    const list = ref([]);

    function addTodo() {
        // 객체 담을 일회용 변수 정의
       const item = {id : Math.random(), todo : msg.value, completed : false};
       
        // 객체 배열에 담기 및 문자열로 변환 -> 객체 배열 자체를 문자열로 변환
        list.value.push(item);
        localStorage.setItem('user', JSON.stringify(list.value));
        addTodoItem();
        msg.value = "";
    }

    // 로직 완성
    onMounted(() => {
        if(localStorage.length > 0) {
            const key = localStorage.getItem('user');
            list.value = JSON.parse(key);
            addTodoItem();
        } 
    })


    const emit = defineEmits(['input-list']);
    function addTodoItem () {
        emit('input-list', list.value);
    }
</script>
    
<style scoped>
#inputTodo {
    width: 400px;
    height: 55px;
    background: white;
    margin: 20px 10px 20px 20px;
    border: 0;
    font-size: 15px;
}
#inputBtn {
    width: 70px;
    height: 55px;
    background: white;
    border: 0;
}
</style>