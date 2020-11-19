<template>
  <TodoForm @add-todo="addTodo" />
  <div class="todo-list">
    <TodoItem 
      v-for="todo in sortedTodos" 
      :key="todo.id" 
      :todoItem="todo"
      @change-todo="changeTodo(todo)"/>
  </div>
</template>

<script>
import TodoItem from './TodoItem'
import TodoForm from './TodoForm'

export default {
  components: {
    TodoItem,
    TodoForm
  },
  data() {
    return {
      todos: [
        { 
          id: 1605715923888, 
          description: 'Learn Vue',
          createdOn: '2020-03-24T18:25:43.511Z',
          finishedOn: null 
        },
        { 
          id: 1605715923889, 
          description: 'Learn Composition API', 
          createdOn: '2020-03-27T18:25:43.511Z', 
          finishedOn: null 
        },
        { 
          id: 1605715923990, 
          description: 'Meeting with Webeetle', 
          createdOn: '2020-05-20T18:25:43.511Z', 
          finishedOn: null 
        }
      ]
    }
  },
  computed: {
    sortedTodos() {
      const toSort = this.todos
      return toSort.sort((e1, e2) => new Date(e2.createdOn) - new Date(e1.createdOn))
    }
  },
  methods: {
    changeTodo(todo) {
      todo.finishedOn = !todo.finishedOn ? new Date() : null
    },
    addTodo(newTodo) {
      const todo = {
        id: Date.now(),
        description: newTodo,
        createdOn: new Date(),
        finishedOn: null
      }

      this.todos.push(todo)
    }
  }
}
</script>

<style scoped>
.todo-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  align-content: center;
  align-self: center;
}


</style>
