<script setup>
import { ref } from 'vue';
defineProps(['content', 'type']);
defineEmits(['remove']);

const isActive = ref(false);

const toggleClass = () => {
  isActive.value = !isActive.value;
}
</script>

<template>
  <div :class="type == 'Персональная' ? 'personal' : 'prof'">
    <span :class="{ active: isActive }">{{ content }}</span>
      <button @click="$emit('remove')" class="deleteBtn">
        <img src="../assets/bin.svg" alt="Удалить" />
      </button>
      <button @click="toggleClass" class="doneBtn">
        <img src="../assets/taskDone.svg" alt="Выполнено">
      </button>
  </div>
</template>

<style scoped>

.active {
  text-decoration: line-through;
}

.personal,
.prof {
  margin-bottom: 1em;
  width: 100%;
  padding-left: 0.3em;
  min-height: 3.8vh;
  /* height: auto; */
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: rgb(242, 242, 242);
  border: 1.5px solid #f72585 !important;
  word-break: break-word;
}

.prof {
  border: 1.5px solid #4361ee !important;
}

span {
  flex-grow: 1;
}

.deleteBtn {
  background-color: rgb(206, 88, 88);
  height: 100%;
  border: none;
  cursor: pointer;
}

.deleteBtn:hover {
  background-color: rgb(206, 88, 88);
  transition: 0.4s;
}

.doneBtn {
  background-color: rgb(83, 171, 83);
  height: 100%;
  border: none;
  cursor: pointer;
}

.doneBtn:hover {
  background-color: rgb(44, 121, 44);
  transition: 0.4s;
}

.doneBtn:active {
  box-shadow: 5px 5px 5px rgb(44, 121, 44);
}

@media (hover: none) {
  .doneBtn:hover {
    background-color: rgb(83, 171, 83);
  }
}

@media screen and (max-width: 1200px) {

  .personal,
  .prof {
    width: 50vw;
  }
}

@media screen and (max-width: 900px) {

  .personal,
  .prof {
    width: 60vw;
  }
}

@media screen and (max-width: 768px) {

  .personal,
  .prof {
    width: 75vw;
  }
}

@media screen and (max-width: 600px) {

  .personal,
  .prof {
    width: 85vw;
  }
}

@media (max-width: 500px) and (max-height: 950px) {

  .personal,
  .prof {
    width: 90vw;
  }
}

@media screen and (max-width: 400px) {

  .personal,
  .prof {
    width: 90vw;
  }
}

@media screen and (max-width: 320px) {

  .personal,
  .prof {
    width: 90vw;
  }
}
</style>
