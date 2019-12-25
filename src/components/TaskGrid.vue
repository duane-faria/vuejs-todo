<template>
  <div class="task-grid">
    <template v-if="tasks.length">
      <task
        v-for="(task,i) in tasks"
        @taskDeleted="$emit('taskDeleted',i)"
        :task="task"
        :key="task.name"
        @stateChanged="$emit('stateChanged',i)"
      ></task>
    </template>
    <p v-else class="no-task">Tudo ok! :D</p>
  </div>
</template>

<script>
import Task from "./Task";
export default {
  components: {
    Task
  },
  props: ["tasks"]
};
</script>

<style>
.task-grid {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.task-grid .task {
  margin: 10px;
}

.no-task {
  color: #aaa;
  font-size: 1.7rem;
}
</style>