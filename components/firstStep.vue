<template>
  <div class="first-step">
    <img src="@/static/bg-pentagon.svg" class="first-step-bg" />
    <div class="upper-items items">
      <Item :item="'scissors'" @select="select" />
    </div>
    <div class="center-items items">
      <Item :item="'spock'" @select="select" />
      <Item :item="'paper'" @select="select" />
    </div>
    <div class="bottom-items items">
      <Item :item="'lizard'" @select="select" />
      <Item :item="'rock'" @select="select" />
    </div>
  </div>
</template>
<script>
import Item from "@/layouts/itemLayout.vue";

export default {
  name: "FirstStepComponent",
  components: {
    Item,
  },
  methods: {
    select(item) {
      this.$emit("start", item)
    }
  }
};
</script>
<style>
.main {
  max-width: 1200px;
  margin: 0 auto;
}
.first-step {
  display: flex;
  flex-direction: column;
  position: relative;
  justify-content: center;
  align-items: center;
  width: clamp(250px, 90%, 400px);
  margin: 4rem auto;
}

.first-step-bg {
  width: clamp(250px, 90%, 400px);
}

.items {
  position: absolute;
  display: flex;
  align-items: center;
}

.upper-items {
  justify-content: center;
  top: -3rem;
  width: 100%;
}

.center-items {
  justify-content: space-between;
  top: calc(40% - 3rem);
  width: 100%;
}

.bottom-items {
  justify-content: space-around;
  width: 100%;
  bottom: -3rem;
}

</style>
