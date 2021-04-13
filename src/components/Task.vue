<template>

    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">

        <h3>
            
            <!-- Title -->
            {{ task.text }}
            
            <!-- Remove Button -->
            <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
            <!-- <i @click="onDelete(task.id)" class="fas fa-times"></i> -->

        </h3>

        <p>{{ task.day }}</p>

    </div>

</template>

<script>

    export default {

        name: 'Task',

        props: {

            task: Object,

        },

        // methods: {

        //     // Method for removing a task
        //     onDelete(id){

        //         this.$emit('delete-task', id);

        //     },

        // },

    }

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