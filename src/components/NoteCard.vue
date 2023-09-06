<script setup> 

const props = defineProps(['noteList'])

</script>
<template>
  <article 
  v-for="note in props.noteList" 
  :key="note.id"
  class="card" 
  :style="{backgroundColor: note.backgroundColor }">
    {{ note.backgroundColor }}

    <p>{{ note.title }}</p>
    <p>{{ note.body }}</p>

    <p>{{ note.date.toLocaleDateString('en-US') }}</p>
  </article>
</template>

<style scoped>
.card {
  border: 1px solid yellow;
  padding:2rem;
  width:24rem;
  background-color: aquamarine;
}
</style>
