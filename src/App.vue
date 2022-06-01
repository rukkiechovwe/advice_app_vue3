<template>
  <AdvicePage :theme="darkMode" :toggleTheme="toggleTheme" />
</template>
<script setup>
import { ref, onMounted } from "vue";
import AdvicePage from "./views/AdvicePage.vue";

const darkMode = ref(false);

onMounted(() => {
  getTheme();
});
function toggleTheme() {
  darkMode.value = !darkMode.value;
  console.log(darkMode.value);
  localStorage.setItem("theme", darkMode.value ? "dark" : "light");
}

function getTheme() {
  const localTheme = localStorage.getItem("theme") ?? "dark";
  darkMode.value = localTheme === "dark" ? true : false;
}
</script>
