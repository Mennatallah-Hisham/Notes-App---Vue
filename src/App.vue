<script setup>
import NoteCard from './components/NoteCard.vue';
import { ref } from 'vue';
import Header from './components/Header.vue';

const openModal=ref(false);
const noteBody=ref("");
const noteTitle=ref("");
const notes =ref([]);

const getRandomColor=()=>{
return "hsl("+Math.random()*360+",70%,75%)";

}
 const resetForm =()=>{
  noteBody.value="";
  noteTitle.value="";
 }

const toggleModal=()=>{
openModal.value=!openModal.value;
}
const addNote=()=>{
  notes.value.push({
    id:Math.floor(Math.random()*1000),
    title:noteTitle.value,
body:noteBody.value,
date:new Date(),
backgroundColor:getRandomColor(),

});

toggleModal();
resetForm();

}

</script>
<template>

  <main>

 <div v-if="openModal" class="overlay">
      <div class="modal">
        <form class="form">
          <input v-model.trim="noteTitle" type="text" placeholder="title"/>

          <textarea v-model="noteBody" name="note" id="note" cols="30" rows="10"></textarea>
          <div class="btns">
            <button @click="addNote" class="form__btn">
              add note
  
            </button> <button  @click="toggleModal" class="form__btn">
         close
  
            </button>
          </div>
         
        </form>
      </div>
    </div> 
    <div class="container">
<Header :btnHandler="toggleModal"></Header>

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
  border:1px solid red;
}



.cards-container{
  display: flex;
  justify-content:left;
  gap:1rem;
  flex-wrap: wrap;
}

.overlay{
  position: absolute;
  width:100%;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.37);
  z-index: 10;
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal{
  background-color: white;
  padding:3rem 6rem;
  border-radius: 0.4rem;
  width:50rem;
}
.form{
  display: flex;
  flex-direction: column;
  gap:1rem;
  width:100%;

}

</style>