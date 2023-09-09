<script setup>
import NoteCard from './components/NoteCard.vue';
import { ref } from 'vue';
import Header from './components/Header.vue';
import Form from"./components/Form.vue";
import {RouterView} from"vue-router";

const openModal=ref(false);
// const noteBody=ref("");
// const noteTitle=ref("");
const notes =ref([]);

const getRandomColor=()=>{
return "hsl("+Math.random()*360+",70%,75%)";

}
//  const resetForm =()=>{
//   noteBody.value="";
//   noteTitle.value="";
//  }

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

</script>
<template>

  <main>
<Form v-if="openModal" :closeModal="toggleModal"  @createNote="addNote"/>
<Header :btnHandler="toggleModal"></Header>

    <div class="container">


      <section
  class="cards-container">

   
<NoteCard :noteList="notes"/>
    

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
  justify-content:left;
  gap:1rem;
  flex-wrap: wrap;
}



</style>