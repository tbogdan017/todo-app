<script setup>
import { ref, onMounted, watch } from 'vue';
import TaskCard from './components/TaskCard.vue';
import TaskCategories from './components/TaskCategories.vue';

const task = ref('');
const myInput = ref(null);
const type = ref('Персональная');
const taskArr = ref([]);
const id = ref(0);

const addTask = () => {
  const newArr = {
    content: task.value,
    type: type.value,
    id: id.value++
  }
  taskArr.value.push(newArr);

  task.value = '';
}

onMounted(() => {
  myInput.value.focus();
})

watch(taskArr, newVal => {
  localStorage.setItem('taskArr', JSON.stringify(newVal));
}, { deep: true });

onMounted(() => {
  taskArr.value = JSON.parse(localStorage.getItem('taskArr')) || [];
})
</script>

<template>
  <header class="upper_panel">
  </header>
  <div class="container">
    <form @submit.prevent="addTask">
      <input ref="myInput" class="user_input" type="text" placeholder="Введите задачу" v-model="task" />
      <span>Выберите категорию</span>

      <TaskCategories v-model="type" />

      <button @click="myInput.focus()" :disabled="task === ''" class="btn" type="submit">Создать задачу</button>
    </form>
    <div class="wrapper">
      <div class="task_block">
        <TaskCard v-for="(taskItem, index) in taskArr" 
        :key="taskItem.id"
        :content="taskItem.content" 
        :type="taskItem.type" 
        @remove="taskArr.splice(index, 1)" />
      </div>
    </div>
  </div>
  <div class="app_info">
    <h2>ToDo App</h2>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&family=Raleway:ital,wght@0,100..900;1,100..900&family=Rubik:ital,wght@0,300..900;1,300..900&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Raleway", sans-serif;
}

p {
  margin-top: 0.5em;
}

h2 {
  margin-top: 0.8em;
}

.app_info {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: grey;
  opacity: 0.3;
}

body {
  background-color: #e9ecef;
}

.upper_panel {
  height: 7vh;
}

.container {
  margin-left: auto;
  margin-right: auto;
  height: 85dvh;
  width: 45vw;
  border-radius: 25px;
  box-shadow: 0px 0px 10px 1px rgba(0, 0, 0, 0.2);
  background: white;
}

form {
  display: grid;
  justify-items: center;
  gap: 1em;
}

.user_input {
  margin-top: 1.5em;
  font-size: 0.95em;
  width: 36.3vw;
  height: 4vh;
  border: 1.5px solid #4361ee;
}

.btn {
  margin: 1em 0;
  width: 36.3vw;
  height: 5vh;
  font-size: 0.95em;
  border: 1px solid #4361ee;
  cursor: pointer;
  background-color: #4361ee;
  color: white;
}

.btn:active {
  border: none;
  background-color: rgb(44, 44, 171);
}

.wrapper {
  overflow: auto;
}

.task_block {
  display: flex;
  flex-direction: column-reverse;
  justify-content: flex-end;
  width: 36.3vw;
  height: 48vh;
  margin-left: auto;
  margin-right: auto;
}

@media screen and (max-width: 1200px) {
  .container {
    width: 55vw;
    font-size: 1.2em;
  }

  .user_input {
    width: 50vw;
    height: 3vh;
  }

  .btn {
    font-size: 0.8em;
    width: 50vw;
    height: 4vh;
  }

  .task_block {
    width: 50vw;
    height: 48vh;
  }
}

@media screen and (max-width: 900px) {
  .container {
    width: 65vw;
  }

  .user_input {
    width: 60vw;
    font-size: 0.8em;
  }

  .btn {
    width: 60vw;
    height: 4vh;
    font-size: 0.8em;
  }

  .task_block {
    width: 60vw;
    height: 55vh;
  }
}

@media screen and (max-width: 768px) {
  .container {
    width: 80vw;
  }

  .user_input {
    width: 75vw;
    font-size: 0.8em;
  }

  .btn {
    width: 75vw;
    height: 4vh;
    font-size: 0.8em;
  }

  .task_block {
    width: 75vw;
    height: 55vh;
  }
}

@media screen and (max-width: 600px) {
  .container {
    width: 90vw;
  }

  .user_input {
    width: 85vw;
    font-size: 0.8em;
  }

  .btn {
    width: 85vw;
    height: 4vh;
    font-size: 0.8em;
  }

  .task_block {
    width: 85vw;
    height: 55vh;
  }
}

@media (max-width: 500px) and (max-height: 950px) {
  .container {
    width: 98vw;
  }

  .user_input {
    width: 90vw;
    height: 3.5vh;
    font-size: 0.9em;
  }

  .btn {
    width: 90vw;
    height: 4vh;
    font-size: 0.8em;
  }

  .task_block {
    width: 90vw;
    height: 40dvh;
  }
}

@media screen and (max-height: 736px) {

  span {
    font-size: 0.8em;
  }

  .user_input {
    font-size: 0.8em;
  }
}

@media screen and (max-width: 400px) {
  .container {
    width: 98vw;
  }

  .btn {
    width: 90vw;
    height: 4vh;
    font-size: 0.75em;
  }

  .task_block {
    width: 90vw;
  }
}
</style>
