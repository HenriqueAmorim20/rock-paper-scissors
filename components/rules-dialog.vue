<template>
  <v-dialog v-model="show" width="500px" :fullscreen="width < 600">
    <v-card class="rules">
      <header>
        <span>Rules</span>
        <v-img
          :src="require('@/static/icon-close.svg')"
          class="close"
          @click="show = false"
        ></v-img>
      </header>
      <v-img :src="require('@/static/image-rules-bonus.svg')"></v-img>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: "RulesDialogComponent",
  props: {
    value: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      width: null,
    };
  },
  computed: {
    show: {
      get() {
        return this.value;
      },
      set(value) {
        this.$emit("input", value);
      },
    },
  },
  mounted() {
    this.width = window.innerWidth;
    this.$nextTick(() => {
      window.addEventListener("resize", this.onResize);
    });
  },
  methods: {
    onResize() {
      this.width = window.innerWidth;
    },
  },
};
</script>

<style scoped>
.rules {
  padding: 2rem !important;
  background-color: hsl(0, 0%, 100%) !important;
  color: var(--darkText) !important;
}

.rules header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 2rem;
}

.rules header span {
  font-size: clamp(1.5rem, 5vw, 2rem);
  text-transform: uppercase;
  font-weight: 700;
}

.rules header .close {
  cursor: pointer;
  max-width: clamp(1.2rem, 5vw, 1.8rem) !important;
}
</style>
