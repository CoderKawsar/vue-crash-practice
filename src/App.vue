<template>
  <Header title="Task Tracker" />

  <main>
    <AddTask @add-task="addTask" />
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </main>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",

  components: {
    Header,
    Tasks,
    AddTask,
  },

  data() {
    return {
      tasks: [],
    };
  },

  created() {
    this.tasks = [
      {
        id: "1",
        text: "Doctors Appointment",
        day: "March 5th at 2:30pm",
        reminder: true,
      },
      {
        id: "2",
        text: "Meeting with boss",
        day: "March 6th at 1:30pm",
        reminder: true,
      },
      {
        id: "3",
        text: "Food shopping",
        day: "March 7th at 2:00pm",
        reminder: false,
      },
    ];
  },

  methods: {
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask];
    },

    deleteTask(id) {
      if (confirm("Are you sure to delete the task?")) {
        this.tasks = this.tasks.filter((task) => task.id != id);
      }
    },

    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },
};
</script>

<style scoped></style>
