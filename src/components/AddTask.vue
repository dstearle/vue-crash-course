<template>

  <form @submit="onSubmit" class="add-form">

    <!-- Task Title Input -->
    <div class="form-control">

        <label>Task</label>

        <input type="text" v-model="text" name="text" placeholder="Add Task" />

    </div>

    <!-- Day & Time Input -->
    <div class="form-control">

      <label>Day & Time</label>

      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />

    </div>

    <!-- Set Reminder Input -->
    <div class="form-control form-control-check">

      <label>Set Reminder</label>

      <input type="checkbox" v-model="reminder" name="reminder" />

    </div>

    <!-- Submit Button -->
    <input type="submit" value="Save Task" class="btn btn-block" />

  </form>

</template>

<script>

    export default {

        name: 'AddTask',

        data() {

            return {

                text: '',
                day: '',
                reminder: false,

            }

        },

        methods: {

            // Method for submitting a new task to the list
            onSubmit(e) {

                // Prevents empty submissions
                e.preventDefault()

                // If task input is empty inform user to fill in
                if(!this.text) {

                    alert('Please add a task')

                    return

                }

                // Creates a new task with the users input
                const newTask = {

                    id: Math.floor(Math.random * 100000),
                    text: this.text,
                    day: this.day,
                    reminder: this.reminder,

                }

                console.log(newTask);

                // Resets the fields after submission
                this.text = ''
                this.day = ''
                this.reminder = false

            },

        },

    }

</script>

<style scoped>

    .add-form {
        margin-bottom: 40px;
    }

    .form-control {
        margin: 20px 0;
    }

    .form-control label {
        display: block;
    }

    .form-control input {
        width: 100%;
        height: 40px;
        margin: 5px;
        padding: 3px 7px;
        font-size: 17px;
    }

    .form-control-check {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .form-control-check label {
        flex: 1;
    }

    .form-control-check input {
        flex: 2;
        height: 20px;
    }

</style>