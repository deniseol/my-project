<template>
  <div class="todo-container">
    <h2>ToDo List</h2>
    <div class="input-container">
      <input v-model="newToDo" placeholder="Add a new todo-item" @keyup.enter="addTodo" />
      <button @click="addTodo">Add</button>
    </div>
    <ul class="card-grid">
      <li v-for="(todo, index) in todos" :key="index" class="card">
        <span>{{ todo.text }}</span>
        <button id="remove" @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
    <p>Total todo-items: {{ todos.length }}</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      newToDo: '',
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newToDo.trim() === '') return;
      this.todos.push({ text: this.newToDo });
      this.newToDo = '';
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style>
.todo-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh; 
  padding: 20px;
}
#remove {
  background-color: #3f0606;
  color: white;
}
.input-container {
  align-self: center;
  gap: 10px;
  margin-bottom: 20px;
}
.card-grid {
  display: grid;
  justify-content: center;
  grid-template-columns: repeat(auto-fit, minmax(200px, 300px));
  gap: 10px;
  list-style-type: none;
  padding: 0;
}
.card {
  min-height: 200px;
  text-align: center;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: rgb(242, 231, 209);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
button {
  background-color: #295408;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 4px;
}
button:hover {
  background-color: #18780c;
}
#remove {
    margin-top: 10px;
  justify-content: baseline;
}
@media (min-width: 1200px) {
  .card-grid {
    grid-template-columns: repeat(auto-fit, minmax(300px, 400px));
  }
  .todo-container {
    min-height: 50vh;
  }
}
</style>
