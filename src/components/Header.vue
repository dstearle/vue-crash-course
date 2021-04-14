<template>

    <header>

        <!-- Title -->
        <h1>{{ title }}</h1>

        <!-- Add Task Button -->
        <Button 
            @toggle-add-task="$emit('toggle-add-task')"
            :text="showAddTask ? 'Close' : 'Add Task'" 
            color="green" 
        />

    </header>

</template>

<script>

    import Button from './Button';

    export default {

        name: 'Header',

        components: { 
            
            Button,
            
        },

        props: {

            title: {

                type: String,
                default: "Task Tracker",

            },
            showAddTask: Boolean,

        },

    }

</script>

<style scoped>

    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }

</style>
