<template>
  <form className="add-form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text">Text</label>
      <input
        type="text"
        id="text"
        name="text"
        v-model.trim="text"
        placeholder="Add Task"
      />
    </div>

    <div class="form-control">
      <label for="day">Day & Time</label>
      <input
        type="text"
        id="day"
        name="day"
        v-model.trim="day"
        placeholder="Add Day & Time"
      />
    </div>

    <div class="form-control form-control-check">
      <label for="reminder">Set Reminder</label>
      <input id="reminder" type="checkbox" name="reminder" v-model="reminder" />
    </div>

    <input type="submit" value="Save Task" className="btn btn-block" />
  </form>
</template>

<script>
import { ref } from '@vue/reactivity';

export default {
  name: 'AddTask',
  setup(_, { emit }) {
    const text = ref('');
    const day = ref('');
    const reminder = ref(false);

    function onSubmit() {
      if (!text.value) {
        alert('Please add a task');
        return;
      }

      const newTask = {
        text: text.value,
        day: day.value,
        reminder: reminder.value,
      };

      emit('add-task', newTask);

      text.value = '';
      day.value = '';
      reminder.value = false;
    }

    return { text, day, reminder, onSubmit };
  },
};
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
  caret-color: green;
}

.form-control input:focus {
  outline: none;
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
