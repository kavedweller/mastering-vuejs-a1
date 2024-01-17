<template>
  <div v-if="showAddTaskPopup">
    <form @submit.prevent="addTask">
      <input type="text" v-model="newTaskName" placeholder="Task Name" />
      <input type="number" v-model="newTaskTime" placeholder="Time (minutes)" />
      <button type="submit">Add Task</button>
    </form>
  </div>
</template>
