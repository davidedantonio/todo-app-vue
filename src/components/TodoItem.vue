<template>
  <div class="todo-item">
    <div class="description">
      {{ todoItem.description }}
      <span class="created-on">(created on {{ moment(todoItem.createdOn).format('DD-MM-YYYY HH:MM') }})</span>
    </div>
    <div class="todo-action">
      <span 
        class="fa"
        :class="[todoItem.finishedOn ? 'fa-check-square checked' : 'fa-square']"
        @click="changeTodo"></span>
    </div>
  </div>
</template>

<script>
import moment from 'moment';

export default {
  props: {
    todoItem: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      moment
    }
  },
  methods: {
    changeTodo() {
      this.$emit('change-todo', this.todoItem)
    }
  }
}
</script>

<style scoped>
.todo-item {
  display: flex;
  flex-direction: row;
  align-items: center;
  align-content: space-between;
  justify-content: space-between;
  margin-bottom: 10px;
  border: 1px solid #c9c9c9;
  padding: 20px;
  width: 40%;
  text-align: left;
  box-sizing: border-box;
}

.description {
  font-size: 1rem;
}

.description > .created-on {
 display: block;
 font-size: .9rem;
 color: #999;
 font-style: italic;
}

.todo-action {
  font-size: 1.3rem;
}

.checked {
  color: #3eaf7c
}
</style>