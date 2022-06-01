<template>
  <div :data-theme="theme ? 'dark' : 'light'">
    <nav class="nav">
      <h4>ADVICE APP</h4>
      <button @click="toggleTheme">
        <svg
          v-if="theme"
          xmlns="http://www.w3.org/2000/svg"
          class="theme"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"
          />
        </svg>
        <svg
          v-else
          xmlns="http://www.w3.org/2000/svg"
          class="theme"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"
          />
        </svg>
      </button>
    </nav>
    <div class="app">
      <AdviceCard
        :id="advice.id"
        :quote="advice.advice"
        :onClick="getAdvice"
        v-if="advice"
      />
      <h1 v-else>Loading...</h1>
    </div>
  </div>
</template>
<script setup>
import { onMounted, ref } from "vue";
import AdviceCard from "../components/AdviceCard.vue";
let advice = ref(null);

const props = defineProps(["theme", "toggleTheme"]);

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
};
</script>
