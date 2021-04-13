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
        
    }

</script>