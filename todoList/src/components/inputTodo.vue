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

------
로직 수정
현재 문제 
입력 컴포넌트에서 입력, 저장, 변환 등 모든 로직 처리하는 중

해결 방안
-> 입력과 동시에 로컬 저장소에 저장하기 때문에 그냥 입력 컴포넌트에서는 메시지 전달만 하고
-> displayList에서 저장, 업데이트, 삭제 등 모든 로직 처리하게 구조 변경하기

로직 꼬인 건 수정 완료
-->

<!-- 
UI 구조 수정
list 박스 전체 크기 (20% 입력 / 80% 출력 컴포넌트로 화면 분할)
대시보드 초기화면 완성하기 -> 프로그레스바 구현
-->

<template> 
<div>
    <input type="text" id="inputTodo" v-model="msg">
    <button id="inputBtn" @click="addTodoItem">Add</button>
</div>
</template>
    
<script setup>
import {ref, defineEmits} from 'vue';

    const msg = ref('');

    const emit = defineEmits(['input-list']);
    function addTodoItem () {
        emit('input-list', msg.value);
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
    height: 57px;
    background: navy;
    color: white;
    border: 0;
    cursor: pointer;
}
</style>