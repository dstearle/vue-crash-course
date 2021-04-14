<template>

    <div class="container">

        <!-- Header -->
        <Header 
            @toggle-add-task="toggleAddTask" 
            :showAddTask="showAddTask"
        />

        <!-- Add Task Form -->
        <div v-show="showAddTask">

            <AddTask @add-task="addTask" />

        </div>

        <!-- Tasks List -->
        <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />

    </div>

</template>

<script>

    import Header from './components/Header.vue';
    import Tasks from './components/Tasks';
    import AddTask from './components/AddTask';

    export default {

        name: 'App',

        components: {

            Header,
            Tasks,
            AddTask,

        },

        data() {

            return {

                tasks: [],
                showAddTask: false,

            }

        },

        async created() {

            this.tasks = await this.fetchTasks()

        },

        // created() {

        //     this.tasks = [

        //         {
        //             id:1,
        //             text: 'Doctors Appointment',
        //             day: 'March 21st at 2:30pm',
        //             reminder: true,
        //         },

        //         {
        //             id:2,
        //             text: '"Masseuse" Appointment',
        //             day: 'April 1st at 12:30am',
        //             reminder: false,
        //         },

        //         {
        //             id:3,
        //             text: 'Take baby to school',
        //             day: 'May 14th at 8:30am',
        //             reminder: true,
        //         },

        //     ]

        // },

        methods: {

            // Method for adding a task
            addTask(task) {

                this.tasks = [...this.tasks, task]

            },

            // Method for removing a task
            deleteTask(id) {

                this.tasks = this.tasks.filter((task) => task.id !== id )

            },

            // Shows or hides the add task form
            toggleAddTask() {

                this.showAddTask = !this.showAddTask

            },

            // Method for toggling the reminder status of a task
            toggleReminder(id) {

                this.tasks = this.tasks.map( (task) => task.id === id ? { ...task, reminder: !task.reminder } : task )

            },

            // Fetches the data from json-server
            async fetchTasks() {

                // The data to be fetched
                const res = await fetch('http://localhost:5000/tasks')

                // The response
                const data = await res.json()

                return data

            },

            // Fetches a single data object from json-server
            async fetchTask() {

                // The data to be fetched
                const res = await fetch(`http://localhost:5000/tasks/${id}`)

                // The response
                const data = await res.json()

                return data

            },

        },

    }

</script>

<style>

    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body {
        font-family: 'Poppins', sans-serif;
    }

    .container {
        max-width: 500px;
        margin: 30px auto;
        overflow: auto;
        min-height: 300px;
        border: 1px solid steelblue;
        padding: 30px;
        border-radius: 5px;
    }

    .btn {
        display: inline-block;
        background: #000;
        color: #fff;
        border: none;
        padding: 10px 20px;
        margin: 5px;
        border-radius: 5px;
        cursor: pointer;
        text-decoration: none;
        font-size: 15px;
        font-family: inherit;
    }

    .btn:focus {
        outline: none;
    }

    .btn:active {
        transform: scale(0.98);
    }

    .btn-block {
        display: block;
        width: 100%;
    }

</style>
