<script setup>
import { ref } from "vue";.


defineProps({
  msg: String,
});

const count = ref(0);
</script>

<script>
import addTask from "./AddTask.vue";
export default {
  components: {
    addTask,
  },
  data() {
    return {
      tasks: ref([
        { name: "Task 1", time: 60 },
        { name: "Task 2", time: 75 },
      ]),
    };
  },
  methods: {
    openAddTaskPopup() {
      this.$refs.addTask.showAddTaskPopup = true;
    },
    handleTaskAdded() {
      this.$refs.addTask.showAddTaskPopup = false;
    },
    addTask(task) {
      this.tasks.push(task);
    },
    removeTask(task) {
      this.tasks.splice(this.tasks.indexOf(task), 1);
    },
  },  
};
</script>

<template>
  <!-- <h1>{{ msg }}</h1> -->

  <div>
    <ul>
      <li v-for="task in tasks" :key="task.name">
        {{ task.name }} ({{ task.time }} minutes)
        <button @click="removeTask(task)">Remove</button>
      </li>
    </ul>
    <button @click="openAddTaskPopup">Add Task</button>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
