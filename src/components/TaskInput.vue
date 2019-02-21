<template>
    <div class="input-group">
      <input
        type="text"
        class="form-control"
        placeholder="Enter a task..."
        v-model="input"
        @keydown.enter.prevent="add"
      />

      <div class="input-group-append">
        <button
          class="btn btn-outline-secondary"
          type="button"
          @click="add"
        >
          Add task
        </button>
      </div>
    </div>
</template>

<script>
export default {
    name: 'task-input',
    data() {
        return {
            input: ''
        }
    },
    computed: {
        trimmedInput() {
            return this.input.trim()
        }
    },
    methods: {
        add() {
            if (this.trimmedInput !== '') {
                this.$emit('taskAdded', this.trimmedInput)
                this.input = ''
            }
        }
    }
}
</script>
