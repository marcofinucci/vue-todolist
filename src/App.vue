<script>
export default {
  name: "App",
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo) {
        this.todos.push({ text: this.newTodo, done: false });
        this.newTodo = "";
      }
    },
  },
};
</script>

<template>
  <div class="container my-20 max-w-lg">
    <!-- Add new todo -->
    <div class="flex">
      <input class="rounded" type="text" v-model="newTodo" placeholder="Nuovo todo" />
      <button class="ml-4 rounded bg-black px-6 text-white" @click="addTodo">Add</button>
    </div>

    <!-- List of todos -->
    <ul class="mt-8">
      <li class="mt-4 flex items-center rounded bg-slate-200 p-4" v-for="(todo, index) in todos" :key="index">
        <input class="rounded border-0" type="checkbox" v-model="todo.done" />
        <div class="ml-3 mr-8">{{ todo.text }}</div>
        <button class="ml-auto text-red-500 underline decoration-1 underline-offset-2" @click="todos.splice(index, 1)">delete</button>
      </li>
    </ul>
  </div>
</template>
