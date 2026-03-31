<!-- 
현재 문제 -> 완료 표시 최신 반영 
qq
computed x
훅 걸기 x 

1. props, emit 써보기
2. 그냥 개수만 받기
-->

<template>
    <div class="dashBorad">
        <div class="title">
        <h1 id="inputTitle">User Info</h1> 
        </div>
        <div class="userinfo">
            <!-- space, margin-left auto -->
            <div class="userData">
                <span> All todo </span><span class="num"> {{ list.length }}</span><br>
            </div>
            <div class="userData">
                <!-- <span> Completed todo</span><span class="num"> {{ props.num }} </span><br> -->
            </div>
            <div class="userData">
                <!-- <span>Not Completed todo</span><span class="num"> {{ list.length }} </span> -->
            </div>    
        </div>
        <div class="progress">
            <!-- 프로그레스바 라이브러리 가져와서 설정 -->
            <RadialProgress
                :diameter="200"
                :completed-steps="completedSteps"
                :total-steps="totalSteps"
                startColor="#3880ff"
                stopColor="#3880ff"
                innerStrokeColor="lightgray"
                >
                <div class="circle_progress_info">
                    <h2>{{ (completedSteps / totalSteps) * 100 }}%</h2>
                </div>
            </RadialProgress>
        </div>
        <!-- 663 -->
    </div>
    
</template>
    
<script setup>
import {ref, onMounted, defineProps, computed} from 'vue'
import RadialProgress from 'vue3-radial-progress';

const completedSteps = ref(125);
const totalSteps = ref(500);

const totalNum = ref(0);
const list = ref([]);

onMounted(() => {
    if(localStorage.length > 0) {
        const key = localStorage.getItem('user');
        list.value = JSON.parse(key);
    } 
})


// 





// const completedTodo = (() => {
//     let count = 0;
//     for(let i=0; i<props.list.length; i++) {
//         if(props.list.completed == true)
//         count++;
//     }

//     return count;
// })


// // props로 업데이트 되는 리스트 게속 받기
// const props = defineProps({
//     list : Array,
// })

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
    height: 50px;
    margin-top: 50px;
}
.userinfo {
    height: 200px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    
}
.progress {
    height: 363px;
}
.userData {
    display: flex;
    justify-content: space-around;
}
.num {
    margin-left: auto;
}
</style>