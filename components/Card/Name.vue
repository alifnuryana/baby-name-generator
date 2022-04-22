<script setup lang="ts">
interface NameCardProps {
  resultName: string[];
}

const props = defineProps<NameCardProps>();

const emits = defineEmits(["delete-name"]);

const handleDelete = (name: string) => {
  emits("delete-name", name);
};
</script>

<template>
  <div class="card" v-for="name in resultName" :key="name">
    <h4>{{ name }}</h4>
    <p @click="handleDelete(name)">x</p>
  </div>
</template>

<style scoped>
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
