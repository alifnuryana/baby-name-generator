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
const names = ref<string[]>([]);
</script>

<template>
  <section>
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" button below</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1) Choose a gender</h4>
        <div class="option-buttons">
          <button
            class="option option-left"
            :class="{ 'option-active': options.gender === Gender.BOY }"
            @click="options.gender = Gender.BOY"
          >
            Boy
          </button>
          <button
            class="option"
            :class="{ 'option-active': options.gender === Gender.UNISEX }"
            @click="options.gender = Gender.UNISEX"
          >
            Unisex
          </button>
          <button
            class="option option-right"
            :class="{ 'option-active': options.gender === Gender.GIRL }"
            @click="options.gender = Gender.GIRL"
          >
            Girl
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose the name's popularity</h4>
        <div class="option-buttons">
          <button
            class="option option-left"
            :class="{
              'option-active': options.popularity === Popularity.TRENDY,
            }"
            @click="options.popularity = Popularity.TRENDY"
          >
            Trendy
          </button>
          <button
            class="option option-right"
            :class="{
              'option-active': options.popularity === Popularity.UNIQUE,
            }"
            @click="options.popularity = Popularity.UNIQUE"
          >
            Unique
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>3) Choose name's length</h4>
        <div class="option-buttons">
          <button
            class="option option-left"
            :class="{ 'option-active': options.length === Length.LONG }"
            @click="options.length = Length.LONG"
          >
            Long
          </button>
          <button
            class="option"
            :class="{ 'option-active': options.length === Length.ALL }"
            @click="options.length = Length.ALL"
          >
            All
          </button>
          <button
            class="option option-right"
            :class="{ 'option-active': options.length === Length.SHORT }"
            @click="options.length = Length.SHORT"
          >
            Short
          </button>
        </div>
      </div>
      <button class="primary">Find Names</button>
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
  margin-bottom: 4rem;
  position: relative;
}

.option-container {
  margin-bottom: 2rem;
}

.option {
  background-color: white;
  outline: 0.15rem solid rgb(249, 87, 89);
  border: none;
  padding: 0.75rem;
  width: 12rem;
  font-size: 1rem;
  color: rgb(27, 60, 138);
  cursor: pointer;
  font-weight: 200;
}

.option-left {
  border-radius: 1rem 0 0 1rem;
}

.option-right {
  border-radius: 0 1rem 1rem 0;
}

.option-active {
  background-color: rgb(249, 87, 89);
  color: white;
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
</style>
