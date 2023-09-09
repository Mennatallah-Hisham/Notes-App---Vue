<script setup>

 defineProps(['btnHandler'])

</script>
<template>
    <header>
        <div class="header-cont">

        
        <h1>Notes</h1>
        <button class="btn-add" @click="btnHandler">+</button>
    </div>
      </header>
</template>

<style scoped>
header{
    padding:2rem  4rem;
 

    background-color: #faf0e6;
  }
  .header-cont{
    max-width: 1200px;
    margin-inline: auto;
    display: flex;
    justify-content: space-between;
  }
  h1{
    font-weight: 800;
    color:black;
  }
  .btn-add{
    background-color: black;
    color:white;
    padding:0.5rem 1.5rem;
    border-radius: 50%;
    font-size: 3rem;
    cursor: pointer;
  }
  .btn-add:hover{
    background-color: rgb(38, 37, 37);
  }
</style>