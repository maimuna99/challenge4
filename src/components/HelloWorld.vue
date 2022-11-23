<script setup>
import { ref } from 'vue';
const response = ref({});

// adding delay
await new Promise((resolve) => {
  setTimeout(() => {
    resolve();
  }, 1000);
});

try {
  const res = await fetch('https://yesno.wtf/api');
  console.log(res);
  response.value = await res.json();
} catch (error) {
  response.value = {
    answer: 'Error! Could not reach the API. ' + error,
    image: '',
  };
}
</script>

<template>
  <p>{{ response.answer }}</p>
  <img :src="response.image" />
</template>
