<template>
  <div :class="[task.reminder ? 'reminder' : '','task']" @dblclick="this.$emit('toggle-reminder', task.id)">
    <h3>{{ task.text }} <i @click="onDelete(task.id)" class="fas fa-times"></i></h3>
    <p>{{ task.day }}</p>
  </div>
</template>
<script>
export default {
  name: 'Task',
  methods: {
    onDelete(id) {
      this.$emit('delete-task', id)
    }
  },
  props: {
    task: Object
  },
  emits: ['delete-task']
}
</script>

<style scope>
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
  .fas {
    color: red;
  }
</style>