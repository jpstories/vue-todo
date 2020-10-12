<template>
  <div class="todo">
    <div class="todo__header">
      <img class="todo__header-logo" alt="Vue logo" :src="logo" />
      <h1 class="todo__header-title">Список задач</h1>
    </div>
    <TodoInput @onAddTask="onAddTask"/>
    <div class="todo__tasks">
      <ListItem
        v-for="(task, index) in tasks"
        :key="index" 
        :index="index"
        :text="task.text"
        :completed="task.completed"
        @onToggleCompleted="onToggleCompleted"
        @onRemoveTask="onRemoveTask"
      />
    </div>
  </div>
</template>

<script>
import logo from "./assets/homework.png";

import ListItem from "./components/ListItem";
import TodoInput from "./components/TodoInput";

export default {
  components: {
    ListItem,
    TodoInput
  },

  props: {
    title: String,
  },

  methods: {

    onToggleCompleted(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    },

    onAddTask(text) {
      this.tasks.push({
        text,
        completed: false
      })
    },

    onRemoveTask(index) {
      this.tasks.splice(index, 1);
    }
  },

  data: () => ({
    tasks: [
      {text: 'Изучить Vue.js', completed: true},
      {text: 'Налить зеленого чаю', completed: false},
    ],
    logo
  })
};
</script>


<style scoped>
@import "./style/style.css";
</style>
