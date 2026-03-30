<!-- 
1. 일단 배열로 객체 받는 거 만들어두기
2. 그리고 일단 로컬에 저장하기
3. 출력은 무조건 객체로 변환시켜서 출력해줘야 함 
-->

<template> 
<div>
    <input type="text" id="inputTodo"><button id="inputBtn">추가하기</button>
    <div class="userInfo">
        <h3>전체 할 일 <span>안녕</span></h3>
        <h3>완료한 일</h3>
        <h3>남은 할 일</h3>
        <span>{{ test2 }}</span>
    </div>
</div>
</template>
    
<script setup>
    import {ref, defineEmits} from 'vue';

    const msg = ref('');
    const test = window.localStorage.setItem('todo1','{id: 1, todo : "안녕", completed : false}');
    const test2 = window.localStorage.getItem('todo1');
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
.userInfo {
    height: 300px;
    width: 500px;
    background: white;
}
</style>