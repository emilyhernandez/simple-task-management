<template>
    <li
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        <span :class="{ 'task-completed': task.completed }">
            {{ task.title}}
          </span>
    
          <!--- TASK BUTTONS -->
          <div class="d-flex">
            <button
              class="btn btn-sm mr-1"
              :class="{ 'btn-success': task.completed, 'btn-outline-success': !task.completed }"
              @click="task.completed = !task.completed"
            >
              &check;
            </button>
    
            <button
              class="btn btn-sm btn-outline-danger"
              @click="remove(task)"
            >
              &times;
            </button>
          </div>
      </li>
</template>

<script>
export default {
    props: ['task'],
    methods: {
        remove(task) {
            this.$emit('taskRemoved', task)
        }
    }
}
</script>



<style lang="scss" scoped>
    .task-completed {
      color: limegreen;
      text-decoration: line-through;
    }
</style>
