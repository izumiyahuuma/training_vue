<script setup lang="ts">
import { PropType } from 'vue';
import { Person } from '../types';

const props = defineProps({
  persons: { type: Object as PropType<Array<Person>> },
});
const emit = defineEmits(['delete-person']);

const deletePerson = (id: number) => {
  emit('delete-person', id);
};
</script>
<template>
  <ul>
    <li v-for="person in persons">
      <span>{{ person.name }}</span>
      <span>{{ person.age }}</span>
      <span><button @click="deletePerson(person.id)">delete</button></span>
    </li>
  </ul>
</template>
<style scoped>
ul {
  background-color: blanchedalmond;
  width: 50%;
  margin-left: auto;
  margin-right: auto;
}
li {
  background-color: burlywood;
  width: 80%;
  margin-left: auto;
  margin-right: auto;
  margin-top: 10px;
  list-style: none;
  display: flex;
  justify-content: space-between;
  padding: 8px 20px;
  font-weight: bold;
}
</style>
