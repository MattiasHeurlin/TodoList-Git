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
                { text: 'Learn Vue', completed: false },
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
  
</template>

<style scoped>

</style>
