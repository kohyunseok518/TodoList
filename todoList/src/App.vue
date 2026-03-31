<template>
  <div class="container">
    <Header>
    </Header>
    <div class="main">
      <DashBoard :listNew="list"/>
      <DisplayList @provide-list="throwList"/>
    </div>
  </div>
</template>
  
<script setup>
  import Header from './components/Header.vue';
  import DisplayList from './components/DisplayList.vue';
  import DashBoard from './components/DashBoard.vue';
  import {ref} from 'vue';

const list = ref([]);

const throwList = ((item) => {
  list.value = item;
})

</script>
  
<style>
  * {
    margin: 0;
    padding: 0px;

  }

  .Header {
    background: rgb(37, 48, 116);
    width: 100%;
    height: 150px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 3rem;
    color: white;

  }
  .main {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .dashBorad {
    width: 45%;
    height: 663px;
    background: #2a4384;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

  }
  .displayList {
    width: 55%;
    height: 663px;
    background: #3255ad;
     display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

  }
</style>