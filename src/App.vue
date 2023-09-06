<script setup>
import NoteCard from './components/NoteCard.vue';
import { ref } from 'vue';

const openModal=ref(false);
const noteBody=ref("");
const noteTitle=ref("");
const notes =ref([]);



const toggleModal=()=>{
openModal.value=!openModal.value;
}
const addNote=()=>{
  notes.value.push({"title":noteTitle.value,
"body":noteBody.value});
toggleModal();

}

</script>
<template>

  <main>

 <div v-if="openModal" class="overlay">
      <div class="modal">
        <form class="form">
          <input v-model="noteTitle" type="text" placeholder="title"/>

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
      <header>
        <h1>Notes {{openModal}}</h1>
        <button class="btn-add" @click="toggleModal">+</button>
      </header>
      <section class="cards-container">
        {{ notes }}
        <NoteCard/>
        <NoteCard/>
        <NoteCard/>
        <NoteCard/>
        <NoteCard/>
        <NoteCard/>

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
header{
  display: flex;
  justify-content: space-between;
  margin-bottom: 3rem;
}
h1{
  font-weight: 800;
}

.btn-add{
  background-color: black;
  color:white;
  padding:0.5rem 1.5rem;
  border-radius: 50%;
  font-size: 3rem;
  cursor: pointer;
}
button:hover{
  background-color: rgb(38, 37, 37);
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