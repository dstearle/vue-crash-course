<template>

    <div class="container">

        <!-- Header -->
        <Header />

        <!-- Tasks -->
        <Tasks @delete-task="deleteTask" :tasks="tasks" />

    </div>

</template>

<script>

    import Header from './components/Header.vue';
    import Tasks from './components/Tasks';

    export default {

        name: 'App',

        components: {

            Header,
            Tasks,

        },

        data() {

            return {

                tasks: []

            }

        },

        created() {

            this.tasks = [

                {
                    id:1,
                    text: 'Doctors Appointment',
                    day: 'March 21st at 2:30pm',
                    reminder: true,
                },

                {
                    id:2,
                    text: '"Masseuse" Appointment',
                    day: 'April 1st at 12:30am',
                    reminder: false,
                },

                {
                    id:3,
                    text: 'Take baby to school',
                    day: 'May 14th at 8:30am',
                    reminder: true,
                },

            ]

        },

        methods: {

            // Method for removing a task
            deleteTask(id){

                console.log('task', id);

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
