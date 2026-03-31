<template>
    <div class="displayList">
        <div id="inputTodo">
            <!-- msg만 받아서 -> 배열에 저장해두기 -> 여기서 불러오기 -->
        <inputTodo @input-list="addTodo"/>
        </div>
        <div class="listBox">
            <div v-for="item in list" class="todoBox">
                <input type="checkbox" name="item" class="todo input" v-model="item.completed">
                <label for="item"> {{ item.todo }} </label>
                <!-- 수정하기 버튼 -->
                 <div class="updateIcon">
                    <span class="material-symbols-outlined" @click="editUp(item)">edit</span>
                    <span class="material-symbols-outlined updateBtn" @click='deleteTodo(item)'>delete</span>
                </div>
            </div>
        </div>
    </div>
</template>
    
<script setup>
import inputTodo from './inputTodo.vue';
import { ref, onMounted, computed, defineEmits, watch } from 'vue';

const list = ref([]);
const editMsg = ref('');

function deleteTodo(item) {
    list.value.splice(item, 1);
    // 다시 배열에 저장
    saveItem();
}

const addTodo = (msg) => {
        // 객체 담을 일회용 변수 정의
       const item = {id : Math.random(), todo : msg, completed : false};
       
        // 객체 배열에 담기 및 문자열로 변환 -> 객체 배열 자체를 문자열로 변환
        list.value.push(item);
        saveItem();
    }

// 앱이 마운트 될 때 로컬 저장소에 데이터 있으면 불러오기
onMounted(() => {
      parseList();
    })

function saveItem() {
    localStorage.setItem('user', JSON.stringify(list.value));
}

// 수정하는 기능
function editUp (item) {
    editMsg.value = prompt('수정할 내용을 입력하세요.')
    item.todo = editMsg.value;
    saveItem();
}

function parseList() {
    if(localStorage.length > 0) {
        const key = localStorage.getItem('user');
        list.value = JSON.parse(key);
    } 
}

// emit
const emits = defineEmits(['provide-list']);

watch(list, () => {
    emits('provide-list',list.value);
    console.log('데이터 발사~');
})

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
    width: 450px;
    height: 70px;
    background: rgb(36, 129, 221);
    margin-bottom: 20px;
    justify-content: space-between;
    display: flex;
    align-items: center;

}

.updateBtn {
    cursor: pointer;
}

#inputTodo {
    height: 110px;
}

.listBox {
    height: 493px;
    overflow: auto;
}
.box {
    box-sizing: border-box;
}

</style>