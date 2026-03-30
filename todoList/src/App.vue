<template>
  <div class="container">
    <Header>
    </Header>
    <div class="main">
      <DashBoard @provide-list="saveList"/>
      <DisplayList :listObj="list"/>
    </div>
  </div>
</template>
  
<script setup>
  import Header from './components/Header.vue';
  import DisplayList from './components/DisplayList.vue';
  import DashBoard from './components/DashBoard.vue';
  import {ref} from 'vue';

  const list = ref([]);
  const saveList = ((list) => {
    list.value = list;
  })

</script>
  
<style>
  * {
    margin: 0px;
    padding: 0px;
  }
  .Header {
    background: #6590FF;
    width: 100%;
    height: 120px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 3rem;
    color: white;
    border: 4px solid navy;
  }
  .main {
    display: flex;
    justify-content: center;
    align-items: center;
    gap : 20px;
  }
  .dashBorad {
    width: 45%;
    height: 603px;
    background: #6590FF;
    margin-top: 30px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 0 10px 10px 0;
    border: 4px solid navy;
  }
  .displayList {
    width: 55%;
    height: 603px;
    background: #6590FF;
    margin-top: 30px;
     display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 10px 0 0 10px;
    border: 4px solid navy;
  }
</style>