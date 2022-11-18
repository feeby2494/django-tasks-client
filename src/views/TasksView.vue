<template>
    <div class="tasks_container">
        <div class="tasks_content">
            <h1>Tasks</h1>
            <ul class="tasks_list">
                <li
                v-for="task in tasks"
                :key="task.id"
                >
                    <h2>{{ task.title }}</h2>
                    <p>{{ task.description }}</p>
                    <button @click="toggleTask(task)">
                        {{ task.completed ? 'Undo' : 'Complete' }}
                    </button>
                    <button @click="deleteTask(task)">Delete</button>
                </li>
            </ul>
        </div>

    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: "TasksView",
    data() {
        return {
            tasks: ['']
        }
    },
    methods: {
        getData() {
            axios
            .get('/api/tasks')
            .then(response => {
                this.tasks = response.data;
            })
            .catch(error => {
                console.log(error)
            })  
        }
    },
    mounted() {
        this.getData();
    }
}

</script>