<template>
    <div class="mb-1">
        <div class="d-flex justify-content-between align-items-center">
            <h3>{{ list.title }}</h3>
            <button 
                class="btn btn-sm btn-outline-danger"
                @click="remove(list)"
            >&times;</button>
        </div>
        
        <ul>
            <task-list-item
                v-for="(task, index) in list.tasks"
                :key="index"
                :task="task"
                @taskRemoved="onTaskRemoved"
                ></task-list-item>
                <task-input @taskAdded="onTaskAdded"/>
        </ul>
        <hr>
    </div>
</template>


<script>
import TaskListItem from './TaskListItem.vue'
import TaskInput from './TaskInput.vue'

export default {
    name: 'task-list',
    components: {
        TaskListItem,
        TaskInput
    },
    props: [
        'list'
    ],
    methods: {
        remove(list) {
            this.$emit('listRemoved', list)
        },
        onTaskRemoved(task) {
            this.list.tasks.splice(this.list.tasks.indexOf(task, 1))
        },
        onTaskAdded(taskName) {
            this.list.tasks.push({ title: taskName, completed: false})
        }
    }
}
</script>
