<template>
  <div class="add-todo">
    <input type="text" v-model="newTodo" />
    <button @click="addTodo">Add Todo</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      newTodo: ''
    }
  },
  methods: {
    addTodo() {
      this.$emit('add-todo', this.newTodo)
      this.newTodo = ''
    }
  }
}
</script>

<style scoped>
.add-todo {
  width: 40%;
  display: flex;
  margin: 0 auto;
  padding: 20px 0;
}

.add-todo > input {
  flex: 2;
  padding: 10px;
  font-size: 1rem;
  margin-right: 10px;
}

.add-todo > button {
  flex: 1;
  font-size: 1rem;
  text-transform: uppercase;
  background: #3eaf7c;
  border: transparent;
  color: #fff;
}
</style>