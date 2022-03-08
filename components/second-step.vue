<template>
  <div class="second-step">
    <div class="user-selection first load-hidden">
      <span>you picked</span>
      <Item :item="user" :width="8.5" />
    </div>
    <div class="result third load-hidden">
      <span>{{ result }}!</span>
      <v-btn class="result-btn" @click="reset()">play again</v-btn>
    </div>
    <div class="user-selection second load-hidden">
      <span>the house picked</span>
      <Item :item="computer" :width="8.5" />
    </div>
  </div>
</template>
<script>
import Item from "@/layouts/itemLayout.vue";

export default {
  name: "SecondSteopComponent",
  components: {
    Item,
  },
  props: {
    user: {
      type: String,
      required: true,
    },
    computer: {
      type: String,
      required: true,
    },
    result: {
      type: String,
      required: true,
    },
  },
  mounted() {
    ScrollReveal().reveal(".first", {
      delay: 200,
      duration: 1000,
      distance: "50px",
      origin: "left",
    });
    ScrollReveal().reveal(".second", {
      delay: 1000,
      duration: 1000,
      distance: "50px",
      origin: "right",
    });
    ScrollReveal().reveal(".third", {
      delay: 2000,
      duration: 1000,
      distance: "50px",
      origin: "bottom",
    });
  },
  methods: {
    reset() {
      this.$emit("reset");
    },
  },
};
</script>
<style scoped>
html.sr .load-hidden {
  visibility: hidden;
}
.second-step {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  margin: 4rem auto;
  max-width: 800px;
}

.user-selection {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
}

.user-selection span {
  font-size: calc(1rem + 1vw);
  text-transform: uppercase;
  margin: 1rem 0;
  min-width: max-content;
}

.result {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 0 2rem;
}

.result span {
  text-transform: uppercase;
  font-size: clamp(1.5rem, 10vw, 2.5em);
  font-weight: 700;
  min-width: max-content;
}

.result-btn {
  background-color: #fff !important;
  color: var(--darkText);
  font-weight: 600;
  padding: 0 3rem !important;
}

@media (max-width: 800px) {
  .second-step {
    grid-template-columns: repeat(2, 1fr);
  }
  .user-selection {
    flex-direction: column-reverse;
  }

  .result {
    grid-row: 2;
    grid-column-start: 1;
    grid-column-end: 3;
  }
}
</style>
