<script setup>
import { ref, onMounted, computed, watch } from "vue";

//refs create a reactive reference to an element in the template
const todos = ref([]);
const name = ref("");

const inputContent = ref("");
const inputCategory = ref(null);

//computed defines computed properties and are reactive
const todosAsc = computed(() =>
  todos.value.sort((a, b) => {
    return b.createdAt - a.createdAt;
  })
);

//watch reactively watches for changes to name
watch(name, (newVal) => {
  localStorage.setItem("name", newVal);
});

//runs after component mounts
onMounted(() => {
  name.value = localStorage.getItem("name") || "";
});

const addTodo = () => {};
</script>

<template>
  <main class="app">
    <section class="greeting">
      <h2 class="title">
        What's up <input type="text" placeholder="name here" v-model="name" />
      </h2>
    </section>

    <section class="create-todo">
      <h3>Create a todo</h3>
      <form @submit.prevent="addTodo">
        <h4>What's on your todo list?</h4>
        <input
          type="text"
          placeholder="e.g. submit assignment"
          v-model="inputContent"
        />
      </form>
    </section>
  </main>
</template>
