<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.remainder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.text }}
      <i
        @click="$emit('delete-task', task.id)"
        class="fa-regular fa-circle-xmark"
      ></i>
    </h3>

    <p>{{ task.time }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {},
  emits: ["delete-task", "toggle-reminder"],
};
</script>

<style scope>
.fas {
  color: red;
}

.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.task.reminder {
  border-left: 5px solid green;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
