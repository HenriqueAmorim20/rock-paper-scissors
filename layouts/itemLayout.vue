<template>
  <div class="item" :id="item" @click="selectItem()">
    <v-img :src="require(`@/static/icon-${item}.svg`)" contain aspect-ratio="1" />
  </div>
</template>
<script>
export default {
  name: "itemLayout.vue",
  props: {
    item: {
      type: String,
      required: true,
    },
  },
  mounted() {
    // Get item element
    const itemElement = document.getElementById(this.item);

    // Sets item border color
    switch (this.item) {
      case "scissors":
        itemElement.style.border = "15px solid #ec9e0e";
        break;
      case "spock":
        itemElement.style.border = "15px solid #40b9ce";
        break;
      case "paper":
        itemElement.style.border = "15px solid #4865f4";
        break;
      case "lizard":
        itemElement.style.border = "15px solid #834fe3";
        break;
      case "rock":
        itemElement.style.border = "15px solid #dc2e4e";
        break;
      default:
        break;
    }
  },
  methods: {
    selectItem() {
      this.$emit("select", this.item)
    }
  }
};
</script>
<style scoped>
.item {
  cursor: pointer;
  border-radius: 50%;
  padding: 3%;
  width: clamp(5.2rem, 25vw, 7.5rem);
  background-color: hsl(0, 0%, 100%);
  box-shadow: 4px 4px 4px hsla(0, 0%, 0%, 0.37);
  transition: transform 0.5s ease;
}

.item:hover {
  transform: scale(1.05);
}
</style>
