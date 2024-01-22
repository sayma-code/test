<template>
  <div class="container">
    <Header title="Hello" />
    <AddTask @add-task = "addTask"/>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import AddTask from './components/AddTask.vue';
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";

export default {
  name: "App",
  components: { Header, Tasks, AddTask },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if (confirm("Sure you want that babe?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task)=> task.id === id ? {...task, remainder: !task.remainder}: task)
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Visit Doctor",
        time: "Today",
        remainder: true,
      },
      {
        id: 2,
        text: "Code",
        time: "Today",
        remainder: true,
      },
      {
        id: 3,
        text: "Code",
        time: "Today",
        remainder: false,
      },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: "Poppins", sans-serif;
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
