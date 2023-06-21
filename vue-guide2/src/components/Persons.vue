<script setup lang="ts">
import { Person } from '../types/person';
import PersonList from './PersonList.vue';
import PersonPostForm from './PersonPostForm.vue';

const person: Person = { id: 1, name: 'hoge', age: 23 };

const persons: Array<Person> = [
  { id: 1, name: 'hoge', age: 23 },
  { id: 2, name: 'dsds', age: 43 },
  { id: 3, name: 'yamada', age: 13 },
];
</script>
<template>
  <PersonPostForm />
  <PersonList :persons="persons" />
</template>
<style scoped></style>
../types/global../@types/person
