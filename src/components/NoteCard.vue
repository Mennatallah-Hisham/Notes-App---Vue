<script setup> 

const props = defineProps(['noteList'])

</script>
<template>
  <article 
  v-for="note in props.noteList" 
  :key="note.id"
  class="card" 
 
  :style="{backgroundColor: note.backgroundColor}">


    <p class="title">{{ note.title }}</p>
    <p>{{ note.body }}</p>

    <p class="date">{{ note.date.toLocaleDateString('en-US') }}</p>
  </article>
</template>

<style scoped>
.card {

  padding:2rem;
  width:24rem;
  color:black;
  border-radius: 2rem;

}
.title{
    text-transform: capitalize;
    font-size: 1.5rem;
    font-weight: 800;
}
.date{
    font-size: 1.1rem;
    font-weight: 600;
}
</style>
