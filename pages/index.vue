<script setup lang="ts">
enum Gender {
  GIRL = "Girl",
  BOY = "Boy",
  UNISEX = "Unisex",
}

enum Populatiry {
  UNIQUE = "Unique",
  TRENDY = "Trendy",
}

enum Length {
  SHORT = "Short",
  ALL = "All",
  LONG = "Long",
}

interface OptionsState {
  gender: Gender;
  popularity: Populatiry;
  length: Length;
}

// const optionsObject: OptionsState = {
//   gender: Gender.UNISEX,
//   popularity: Populatiry.UNIQUE,
//   length: Length.ALL,
// };

const options = reactive<OptionsState>({
  gender: Gender.UNISEX,
  popularity: Populatiry.UNIQUE,
  length: Length.ALL,
});
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
              'option-active': options.popularity === Populatiry.TRENDY,
            }"
            @click="options.popularity = Populatiry.TRENDY"
          >
            Trendy
          </button>
          <button
            class="option option-right"
            :class="{
              'option-active': options.popularity === Populatiry.UNIQUE,
            }"
            @click="options.popularity = Populatiry.UNIQUE"
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
</style>
