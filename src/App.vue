<script setup>
import NoteCard from './components/NoteCard.vue';
import { ref } from 'vue';
import Header from './components/Header.vue';
import Form from"./components/Form.vue";


const openModal=ref(false);

const notes =ref([]);

const getRandomColor=()=>{
return "hsl("+Math.random()*360+",70%,90%)";

}


const toggleModal=()=>{
openModal.value=!openModal.value;
}
const addNote=(title, body)=>{
 
  notes.value.push({
    id:Math.floor(Math.random()*1000),
    title:title,
body:body,
date:new Date(),
backgroundColor:getRandomColor(),

});

toggleModal();


}
const deleteNote=(id)=>{

  notes.value=notes.value.filter((note)=>note.id!==id);
}

</script>
<template>

  <main>
<Form v-if="openModal" :closeModal="toggleModal"  @createNote="addNote"/>
<Header :btnHandler="toggleModal"></Header>

    <div class="container">


      <section
  class="cards-container">

   
<NoteCard :noteList="notes" @delete="deleteNote"/>
    

      </section>
    </div>
  </main>
</template>

<style scoped>
main{
  height:100vh;

  
}
.container{
  max-width: 1200px;
  margin-inline: auto;
  padding:2rem 5rem;

}



.cards-container{
  display: flex;
  justify-content:center;
  gap:3rem;
  flex-wrap: wrap;

}



</style>