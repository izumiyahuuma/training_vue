<script setup lang="ts">
import { defineProps, defineEmits } from 'vue';
type Tweet = {
  id: number;
  description: string;
};
type Props = {
  tweets: Tweet[];
};
const emit = defineEmits(['delete-tweet']);
const deleteTweet = (id: number) => {
  emit('delete-tweet', id);
};

defineProps<Props>();
</script>
<template>
  <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
    <span>{{ tweet.description }}</span>
    <button class="delete-button" @click="deleteTweet(tweet.id)">remove</button>
  </li>
</template>
<style scoped>
.delete-button {
  color: #fff;
  font-weight: bold;
  background-color: #ff6f00;
  border-radius: 2px;
  border: none;
  width: 60px;
  height: 22px;
}

.tweet-list {
  list-style: none;
}
</style>
