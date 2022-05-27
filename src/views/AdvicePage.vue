<template>
  <AdviceCard
    :id="advice.id"
    :quote="advice.advice"
    :onClick="getAdvice"
    v-if="advice"
  />
  <h1 v-else>Loading...</h1>
</template>
<script setup>
import { onMounted } from "vue";
import { ref } from "vue";
import AdviceCard from "../components/AdviceCard.vue";
let advice = ref(null);

onMounted(() => {
  getAdvice();
});

const getAdvice = async () => {
  try {
    const res = await fetch(`https://api.adviceslip.com/advice`);
    const json = await res.json();
    advice.value = json.slip;
    console.log(advice.value);
  } catch (err) {
    console.log(err);
  }

  return { advice, getAdvice };
};
</script>
