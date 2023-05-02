<script setup>
import { ref, onMounted, computed, watch } from 'vue';

//refs create a reactive reference to an element in the template
const todos = ref([]);
const name = ref('');

const inputContent = ref('');
const inputCategory = ref(null); 

//computed defines computed properties and are reactive
const todosAsc = computed(() => todos.value.sort((a,b) => {
  return b.createdAt - a.createdAt;
})); 

</script>

<template>
 <main class="app">
  <section class="greeting">
    <h2 class="title">
      What's up <input type='text' placeholder="name here" v-model="name"/>
    </h2>
  </section>
 </main>
</template>


