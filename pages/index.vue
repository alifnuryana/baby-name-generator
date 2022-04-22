<script setup lang="ts">
import { Popularity, Gender, Length, names } from "@/data/data";

interface OptionsState {
  gender: Gender;
  popularity: Popularity;
  length: Length;
}

// Option State
const options = reactive<OptionsState>({
  gender: Gender.UNISEX,
  popularity: Popularity.UNIQUE,
  length: Length.ALL,
});

// Names State
const resultName = ref<string[]>([]);

const computeResultNames = () => {
  const filteredNames = names
    .filter((name) => name.gender === options.gender)
    .filter((name) => name.popularity === options.popularity)
    .filter((name) => {
      if (options.length === Length.ALL) return true;
      else return name.length === options.length;
    });
  resultName.value = filteredNames.map((name) => name.name);
  window.scrollTo(0, document.body.scrollHeight);
};

const optionsArray = [
  {
    title: "1) Choose a gender",
    category: "gender",
    buttons: [Gender.BOY, Gender.UNISEX, Gender.GIRL],
  },
  {
    title: "2) Choose the name's popularity",
    category: "popularity",
    buttons: [Popularity.TRENDY, Popularity.UNIQUE],
  },
  {
    title: "3) Choose name's length",
    category: "length",
    buttons: [Length.SHORT, Length.ALL, Length.LONG],
  },
];
</script>

<template>
  <section>
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" button below</p>
    <div class="options-container">
      <Option
        v-for="option in optionsArray"
        :key="option.title"
        :option="option"
        :options="options"
      />
      <button class="primary" @click="computeResultNames">Find Names</button>
    </div>
    <div class="cards-container">
      <CardName :resultName="resultName" />
      <!-- <div class="card" v-for="name in resultName" :key="name">
        <h4>{{ name }}</h4>
        <p>x</p>
      </div> -->
    </div>
  </section>
</template>

<style scoped>
h1 {
  font-size: 3rem;
}

.options-container {
  background-color: rgb(255, 238, 236);
  border-radius: 2rem;
  padding: 1rem;
  padding-bottom: 2rem;
  width: 95%;
  margin: 0 auto;
  margin-top: 4rem;
  position: relative;
}

.primary {
  background-color: rgb(249, 87, 89);
  color: white;
  border-radius: 6.5rem;
  border: none;
  padding: 0.75rem 4rem;
  font-size: 1rem;
  margin-top: 1rem;
  cursor: pointer;
}

.cards-container {
  display: flex;
  justify-content: center;
  margin-top: 3rem;
  flex-wrap: wrap;
}

.card {
  background-color: rgb(27, 60, 138);
  width: 28%;
  color: white;
  border-radius: 1rem;
  padding: 0.1rem;
  margin-right: 0.5rem;
  margin-bottom: 1rem;
  position: relative;
}

.card p {
  position: absolute;
  width: 1.2rem;
  text-align: center;
  border-radius: 50%;
  top: -32%;
  left: 92.5%;
  cursor: pointer;
  color: rgb(27, 60, 138);
  background-color: rgb(249, 87, 89);
}
</style>
