<template>
  <div class="main">
    <Header :score="score" />
    <FirstStep v-if="currentStep === 1" @start="start" />
    <SecondStep
      v-if="currentStep === 2"
      :user="userItem"
      :computer="computerItem"
      :result="result"
      @reset="reset"
    />

    <v-btn class="rules" @click="showRules = true"> Rules </v-btn>
    <RulesDialog v-model="showRules" />
  </div>
</template>

<script>
import Header from "@/layouts/header.vue";

export default {
  name: "IndexPage",
  components: {
    Header,
  },
  data() {
    return {
      items: ["scissors", "spock", "paper", "lizard", "rock"],
      result: "",
      computerItem: null,
      userItem: null,
      showRules: false,
      currentStep: 1,
      score: 0,
    };
  },
  mounted() {
    this.score = parseInt(window.localStorage.getItem("score")) || 0;
  },
  methods: {
    // Starts the game, checks the result and changes the current step view
    start(itemSelectedUser) {
      this.userItem = itemSelectedUser;
      this.computerItem = this.generateComputerItem(this.userItem);
      this.checkResult();
      this.currentStep = 2;
    },

    // Returns a random value from the 5 possible item options
    generateComputerItem() {
      return this.items[Math.floor(Math.random() * 5)];
    },

    // Checks if the user won or lost based on game rules
    checkResult() {
      // Draw
      if (this.userItem === this.computerItem) return (this.result = "draw");

      // Sets result to true if the user wins and to false if the user loses according to the game rules
      switch (this.userItem) {
        // Scissors beats paper and lizard
        case this.items[0]:
          this.result =
            this.computerItem === this.items[2] ||
            this.computerItem === this.items[3];
          break;
        // Spock beats scissors and rock
        case this.items[1]:
          this.result =
            this.computerItem === this.items[0] ||
            this.computerItem === this.items[4];
          break;
        // Paper beats rock and spock
        case this.items[2]:
          this.result =
            this.computerItem === this.items[1] ||
            this.computerItem === this.items[4];
          break;
        // Lizard beats spock and paper
        case this.items[3]:
          this.result =
            this.computerItem === this.items[1] ||
            this.computerItem === this.items[2];
          break;
        // Rock beats lizard and scissors
        case this.items[4]:
          this.result =
            this.computerItem === this.items[0] ||
            this.computerItem === this.items[3];
          break;
        default:
          console.log("error");
          break;
      }

      // Sets the correct text to the result variable and increments the score if the user won
      if(this.result) {
        this.result = "you win"
        this.score++
        window.localStorage.setItem("score", this.score)
      } else{
        this.result = "you lose"
      }
    },

    // Resets the game back to first step
    reset() {
      this.currentStep = 1;
    },
  },
};
</script>

<style scoped>
.main {
  max-width: 1000px;
  margin: 0 auto;
}

.current {
  opacity: 1;
  transition: opacity 3s ease;
}

.hidden {
  opacity: 0;
  transition: opacity 0.5s ease;
}

.rules {
  box-shadow: none;
  border: 1px solid var(--headerOutline);
  background-color: transparent !important;
  padding: 0 2rem !important;
  margin: 0 2rem;
  font-size: 1.1rem;
}

@media (max-width: 700px) {
  .main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
}
</style>
