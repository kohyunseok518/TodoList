<!-- 
현재 문제 -> 완료 표시 최신 반영 
qq
computed x
훅 걸기 x 

1. props, emit 써보기
2. 그냥 개수만 받기


배열이 추가될때 총 길이가 늘어나야람
체크표시가 된 목록이 생기면 completed 숫자 올라가기

-->

<template>
    <div class="dashBorad">
        <div class="title">
            <h1 id="inputTitle">User Info</h1> 
        </div>
        <div class="userinfo">
            <!-- space, margin-left auto -->
            <div class="userData">
                <span> All todo </span><span class="num"> {{ props.listNew.length }}</span><br>
            </div>
            <div class="userData">
            <span> Completed todo</span><span class="num"> {{ completedTodo }} </span><br>
            </div>
            <div class="userData">
                <span>Not Completed todo</span><span class="num"> {{ props.listNew.length - completedTodo }} </span>
            </div>    
        </div>
        <div class="progress">
            <!-- 프로그레스바 라이브러리 가져와서 설정 -->
            <RadialProgress
                :diameter="200"
                :completed-steps="completedTodo"
                :total-steps="props.listNew.length"
                startColor="#3880ff"
                stopColor="#3880ff"
                innerStrokeColor="lightgray"
                >
                <div class="circle_progress_info">
                    <h2>{{ (completedTodo / props.listNew.length) * 100 }}%</h2>
                </div>
            </RadialProgress>
        </div>
        <!-- 663 -->
    </div>
    
</template>

<script setup>
import {ref, onMounted, defineProps, computed, onUpdated} from 'vue'
import RadialProgress from 'vue3-radial-progress';

const list = ref([]);



onMounted(() => {
    parseList();
})

onUpdated(() => {
    parseList();
})

function parseList() {
    if(localStorage.length > 0) {
        const key = localStorage.getItem('user');
        list.value = JSON.parse(key);
    } 
}

const completedTodo = computed(() => {
    let count = 0;
    for(let item of props.listNew) {
        if(item.completed === true) {
            count ++;
        }
    }

    return count;
})


// props로 업데이트 되는 리스트 게속 받기
const props = defineProps({
    listNew : Array,
})

// 무한 업데이트 훅 오류 발생 -> watch로 배열이 업데이트 될 시에만 list, localstorage 변경되게 수정
// onUpdated(() => {
//     if(localStorage.length > 0) {
//         const key = localStorage.getItem('user');
//         list.value = JSON.parse(key);
//     } 
// })

// watch도 오류남
// watch(localStorage.getItem('user'),() => {
//     if(localStorage.length > 0) {
//         const key = localStorage.getItem('user');
//         list.value = JSON.parse(key);
//     } 
// })
</script>
    
<style scoped>
#inputTitle {
    color: white;
}
.title {
    height: 70px;
    margin-top: 30px;
}
.userinfo {
    width: 380px;
    height: 200px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    margin-top: 20px;
    
}
.progress {
    height: 363px;
    display: flex;
    align-items: center;
}
.userData {
    display: flex;
    justify-content: space-around;
}
.num {
    margin-left: auto;
}

.userData span {
    color: white;
    font-size: 25px;
}
</style>