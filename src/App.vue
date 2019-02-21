<template>
  <div id="app" class="container mt-2" style="max-width: 768px;">
    
    <list-input @listAdded="onListAdded"/>
    
    <template v-if="lists.length == 0">
      <hr>
      <span>Start by creating a new task list.</span>
      <hr>
    </template>
    <template v-else>
      <hr>
    </template>
    
    <task-list 
      v-for="(list, index) in lists"
      :key="index"
      :list="list"
      @listRemoved="onListRemoved"
    />

  </div>
</template>

<script>
import TaskList from './components/TaskList.vue'
import ListInput from './components/ListInput.vue'

export default {
  name: 'app',
  components: {
    TaskList,
    ListInput
  },
  data() {
    return {
      lists: []
    }
  },
  methods: {
    onListAdded(listName) {
        this.lists.push({title: listName, tasks: []})
    },
    onListRemoved(list) {
      this.lists.splice(this.lists.indexOf(list), 1)
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
