<script setup> 

const props = defineProps(['noteList'])
const emit =defineEmits(['delete']);

</script>
<template>
  <div  v-for="note in props.noteList" 
  :key="note.id"
  class="card" 
 
  :style="{backgroundColor: note.backgroundColor}">

  <article 
 >


    <p class="title">{{ note.title }}</p>
    <p class="body">{{ note.body }}</p>
    <div class="card-footer">
      <p class="date">{{ note.date.toLocaleDateString('en-US') }}</p>
      <button
      class="btn-filled"
       @click="$emit('delete',note.id)">delete</button>
   
     
    </div>
  
       

  </article>
</div>
</template>

<style scoped>
.card {

  padding:2rem;
  width:24rem;
  color:black;
  border-radius: 2rem;

  overflow: hidden;

}
.title{
    text-transform: capitalize;
    font-size: 1.5rem;
    font-weight: 800;
}
.body{
  padding:1rem 0;
}
.card-footer{
  margin-top:3rem;
  display: flex;
  justify-content: space-between;
  align-items: flex-end;

}
.date{
    font-size: 1.2rem;
    font-weight: 600;




}
</style>
