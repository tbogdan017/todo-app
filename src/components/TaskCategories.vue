<script setup>
const model = defineModel();
</script>

<template>
    <div class="categories">
        <div class="categ_personal">
          <input type="radio" id="radio_one" value="Персональная" v-model="model"  />
          <label for="radio_one">Персональная</label>
        </div>

        <div class="categ_prof">
          <input type="radio" id="radio_two" value="Профессиональная" v-model="model"  />
          <label for="radio_two">Профессиональная</label>
        </div>
      </div>
</template>

<style scoped>
.categories {
  display: flex;
  width: 36.3vw;
  justify-content: flex-end;
}

.categ_personal,
.categ_prof {
  display: grid;
  align-items: center;
  justify-items: center;
  width: 50%;
  height: 8vh;
  border: 1.5px solid #4361ee;
  border-radius: 5px;
  background-color: rgb(242, 242, 242);
}

.categ_personal {
  margin-right: 1em;
  border: 1.5px solid #f72585;
}


.categ_personal:hover,
.categ_prof:hover {
  background-color: rgb(201, 201, 201);
  transition: .5s;
}

@media screen and (max-width: 1200px) {
  .categories {
    width: 50vw;
  }
}

@media screen and (max-width: 900px) {
  .categories {
    width: 60vw;
  }
}

@media screen and (max-width: 768px) {
  .categories {
    width: 75vw;
  }
}

@media screen and (max-width: 600px) {
  .categories {
    width: 85vw;
  }
}

@media (max-width: 500px) and (max-height: 950px) {
  .categories {
    width: 90vw;
    font-size: 0.9em;
  }
}

@media screen and (max-width: 400px) {
  .categories {
    width: 90vw;
    font-size: 0.75em;
  }
}
</style>