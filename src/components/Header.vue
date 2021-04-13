<template>

    <header>

        <!-- Title -->
        <h1>{{ title }}</h1>

        <!-- Add Task Button -->
        <Button text="Add Task" color="green" />

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
