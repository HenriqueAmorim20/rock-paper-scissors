<template>
  <header>
    <img
      src="@/static/logo-bonus.svg"
      alt="rock-paper-scissor-lizard-spock"
      class="logo-img"
    />
    <div class="score">
      <span>SCORE</span>
      <p id="score-number">12</p>
    </div>
  </header>
</template>
<script>
export default {
  name: "HeaderLayout",
};
</script>
<style scoped>
header {
  display: flex;
  width: clamp(300px, 90%, 700px);
  min-width: 320px;
  justify-content: space-between;
  margin: 1rem auto;
  border: 2px solid var(--headerOutline);
  border-radius: 15px;
  padding: 1rem;
}

.score {
  background-color: #fff;
  width: max(20%, 100px);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  border-radius: 0.5rem;
}

.score span {
  color: var(--darkText);
  font-size: 1.1rem;
  margin: 0 0 -0.7rem;
}

.score p {
  margin: -0.7rem 0 0;
  padding: 0;
  color: var(--darkText);
  font-size: 4rem;
}
</style>
