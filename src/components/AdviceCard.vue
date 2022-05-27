<template>
  <div class="advice">
    <h4 class="id">ADVICE #{{ id }}</h4>
    <h2 class="quote">{{ quote }}</h2>
    <img src="../assets/images/pattern-divider-desktop.svg" class="divider" />
    <button class="dice" @click.prevent="onClick">
      <img src="../assets/images/icon-dice.svg" />
    </button>
  </div>
</template>
<script>
export default {
  name: "AdviceCard",
  props: ["quote", "id", "onClick"],
};
</script>
<style scoped>
.advice {
  background: var(--dark-grayish-blue);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  width: calc(444px + 4rem);
  border-radius: 10px;
  text-align: center;
  position: relative;
}
.id {
  color: var(--neon-green);
  font-size: 13px;
  letter-spacing: 3px;
}
.quote {
  color: var(--light-cyan);
  font-size: 26px;
  font-family: "ManropeBold";
  padding: 1rem 0 2rem;
  font-weight: 500;
}
.divider {
  padding: 0 0 2.5rem;
}
.dice {
  position: absolute;
  bottom: -23px;
  background: var(--neon-green);
  padding: 18px;
  border-radius: 50%;
  height: 60px;
  width: 60px;
}
.dice:hover {
  -webkit-box-shadow: 0px 0px 20px 0 rgb(82, 255, 168);
  -moz-box-shadow: 0px 0px 20px 0 rgb(82, 255, 168);
  box-shadow: 0px 0px 20px 0 rgb(82, 255, 168);
}
@media screen and (max-width: 475px) {
  .quote {
    font-size: 20px;
    padding: 1rem 0;
  }
  .advice {
    width: 100%;
    padding: 2rem 1rem;
  }
  .dice {
    height: 45px;
    width: 45px;
    padding: 13px;
  }
  .divider {
    padding: 0 0 1rem;
  }
}
@media screen and (min-width: 1024px) {
  .quote {
    font-size: 26px;
  }
  .advice {
    width: calc(444px + 6rem);
  }
}
</style>
