<template>
  <div
    class="item"
    @click="selectItem()"
    :style="`width: clamp(${width}rem, 25vw, ${
      width + 2
    }rem); border: 15px solid ${color}`"
  >
    <v-img
      :src="require(`@/static/icon-${item}.svg`)"
      contain
      aspect-ratio="1"
    />
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
    width: {
      type: Number,
      default: 5.5,
    },
  },
  data() {
    return {
      color: "#fff",
    };
  },
  mounted() {
    // Sets item border color
    switch (this.item) {
      case "scissors":
        this.color = "#ec9e0e";
        break;
      case "spock":
        this.color = "#40b9ce";
        break;
      case "paper":
        this.color = "#4865f4";
        break;
      case "lizard":
        this.color = "#834fe3";
        break;
      case "rock":
        this.color = "#dc2e4e";
        break;
      default:
        this.color = "#fff";
        break;
    }
  },
  methods: {
    selectItem() {
      this.$emit("select", this.item);
    },
  },
};
</script>
<style scoped>
.item {
  cursor: pointer;
  border-radius: 50%;
  padding: 10px;
  background-color: hsl(0, 0%, 100%);
  box-shadow: 4px 4px 4px hsla(0, 0%, 0%, 0.37);
  transition: transform 0.5s ease;
}

.item:hover {
  transform: scale(1.05);
}
</style>
