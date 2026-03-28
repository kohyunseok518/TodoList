<template>
  <div class="container">
    <div class="Header">
        <span>Todo List</span>
    </div>
    <div class="main">
      <div class="dashBorad"></div>
      <div class="displayList"></div>
    </div>
  </div>
</template>
  
<script setup>
  
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
  }
  .main {
    display: flex;
    justify-content: center;
    align-items: center;
    gap : 20px;
  }
  .dashBorad {
    width: 35%;
    height: 603px;
    background: #6590FF;
    margin-top: 30px;
  }
  .displayList {
    width: 65%;
    height: 603px;
    background: #6590FF;
    margin-top: 30px;
  }
</style>