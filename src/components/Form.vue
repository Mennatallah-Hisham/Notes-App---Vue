<script setup>
import { ref } from 'vue';
defineProps(['closeModal',"addNote"]);
// const emit = defineEmits('createNote');
const noteBody=ref("");
const noteTitle=ref("");


</script>

<template>
    <div  class="overlay">
        <div class="modal">
          <!-- <form  class="form"> -->
            <input v-model.trim="noteTitle" type="text" placeholder="title"/>
            {{ noteTitle }}
  
            <textarea v-model="noteBody" name="note" id="note" cols="30" rows="10"></textarea>
            <div class="btns">

              <button @click="$emit('createNote',noteTitle,noteBody)" class="form__btn">
                add note
    
              </button> 
              <button  @click="closeModal" class="form__btn">
           close
    
              </button>
            </div>
           
          <!-- </form> -->
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
  .form{
    display: flex;
    flex-direction: column;
    gap:1rem;
    width:100%;
  
  }
</style>