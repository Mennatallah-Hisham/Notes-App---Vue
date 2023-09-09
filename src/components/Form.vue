<script setup>
import { ref } from 'vue';
defineProps(['closeModal']);

const noteBody=ref("");
const noteTitle=ref("");



</script>

<template>
    <div  class="overlay">
        <div class="modal">
            <h1> create new note</h1>
          <form @submit.prevent="$emit('createNote',noteTitle,noteBody)" class="form">
       
                <input v-model.trim="noteTitle" type="text" placeholder="title" required/>
               
            

    <textarea v-model="noteBody" name="note" id="note" cols="30" rows="10" required></textarea>
  
            
            <div class="btns">

              <button  class="btn-filled">
                add note
    
              </button> 
              <button @click="closeModal" class="btn-outline">
           close
    
              </button>
            </div>
           
          </form>
        </div>
      </div> 
</template>

<style scoped>
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
  h1{
    color:black;
    text-transform: capitalize;
    margin-bottom: 1rem;
  }
  .form{
    display: flex;
    flex-direction: column;
    gap:1rem;
    width:100%;
  
  }
  .btns{
    display: flex;
    justify-content: flex-end;
    gap:1rem;

  }
 

</style>