<script setup>

 defineProps(['btnHandler'])

</script>
<template>
    <header>
        <h1>Notes</h1>
        <button class="btn-add" @click="btnHandler">+</button>
      </header>
</template>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    margin-bottom: 3rem;
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