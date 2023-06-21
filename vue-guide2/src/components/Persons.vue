<script setup lang="ts">
import { Ref, ref } from 'vue';
import { Person } from '../types/person';
import PersonList from './PersonList.vue';
import PersonPostForm from './PersonPostForm.vue';

const persons: Ref<Array<Person>> = ref([
  { id: 1, name: 'hoge', age: 23 },
  { id: 2, name: 'dsds', age: 43 },
  { id: 3, name: 'yamada', age: 13 },
]);

const deletePerson = (id: number) => {
  persons.value = persons.value.filter((p) => p.id !== id);
};
</script>
<template>
  <PersonPostForm />
  <PersonList :persons="persons" @delete-person="deletePerson" />
</template>
<style scoped></style>
