<template>
    <div class="input-group">
    <input
      type="text"
      class="form-control"
      placeholder="Create new task list..."
      v-model="input"
      @keydown.enter.prevent="add"
    >
    <div class="input-group-append">
        <button
          class="btn btn-outline-secondary"
          type="button"
          @click="add"
        >
          Create list
        </button>
      </div>
  </div>
</template>

<script>
export default {
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
                this.$emit('listAdded', this.trimmedInput)
                this.input = ''
            }
        }
    }
}
</script>
