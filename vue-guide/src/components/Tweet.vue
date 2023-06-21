<script setup lang="ts">
import { ref } from 'vue';
import TweetPostForm from './TweetPostForm.vue';
import TweetList from './TweetList.vue';

const tweets = ref([
  { id: 0, description: 'hello' },
  { id: 1, description: 'hello fuga' },
  { id: 2, description: 'hello hoge' },
]);
// const inputtingDescription = ref<string>('');

const postTweet = (description: string) => {
  const max = tweets.value.reduce((a, b) => (a.id > b.id ? a : b));
  const tweet = {
    id: max.id + 1,
    description,
  };
  tweets.value.push(tweet);
};
const deleteTweet = (id: number) => {
  tweets.value = tweets.value.filter((v) => v.id !== id);
};
</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <TweetPostForm @post-tweet="postTweet" />
    <div class="tweet-container">
      <p v-if="tweets.length === 0">No tweets have peen added</p>
      <ul>
        <TweetList :tweets="tweets" @delete-tweet="deleteTweet" />
      </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
