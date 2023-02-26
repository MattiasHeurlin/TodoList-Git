<script lang="ts">
  import { defineComponent, reactive } from 'vue'

  export default defineComponent({
    name: 'TodoApp',
    setup() {

    interface Todo {
      text: string,
      done: boolean
    }

    const state = reactive({
              todos: [
                { text: 'Become VueMaster', completed: false },
                { text: 'Build an app', completed: false },
                { text: 'Deploy app to production', completed: false }
              ],
               newTodoText: '',
              });
              function addNewTodo() {
                state.todos.push({
                  text: state.newTodoText,
                  completed: false
                });
                state.newTodoText = '';
              }
              function removeTodo(index: number) {
                state.todos.splice(index, 1);
              }
              function toggleTodoStatus(index: number) {
                state.todos[index].completed = !state.todos[index].completed;
              }


      return {
        state,
        addNewTodo,
        removeTodo,
        toggleTodoStatus

      }
    }
  })
  
</script>

<template>
  <main>
    <h1>Todo App</h1>
    <input type="text" v-model="state.newTodoText" />
    <button @click="addNewTodo">Add Todo</button>
    <ul>
      <li v-for="(todo, index) in state.todos" :key="index">
        <input type="checkbox" :checked="todo.completed" @change="toggleTodoStatus(index)" />
        <span :class="{ 'line-through': todo.completed }">{{ todo.text }}</span>
        <button @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
  </main>
</template>

<style scoped>
  .line-through {
    text-decoration: line-through;
  }
</style>
