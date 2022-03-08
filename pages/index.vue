<template>
  <div class="main">
    <FirstStep @start="start" />
    <v-btn class="rules" @click="showRules = true"> Rules </v-btn>
    <RulesDialog v-model="showRules" />
  </div>
</template>

<script>
import RulesDialog from "@/components/rules-dialog.vue"
export default {
  name: "IndexPage",
  components: {
    RulesDialog,
  },
  data() {
    return {
      items: ["scissors", "spock", "paper", "lizard", "rock"],
      result: null,
      computerItem: null,
      userItem: null,
      showRules: false,
    };
  },
  methods: {
    start(itemSelectedUser) {
      this.userItem = itemSelectedUser;
      this.computerItem = this.generateComputerItem(this.userItem);
      this.result = this.checkResult();
      console.log(this.userItem);
      console.log(this.computerItem);
      console.log(this.result);
    },

    // Returns a random value from the 5 possible item options
    generateComputerItem() {
      return this.items[Math.floor(Math.random() * 5)];
    },

    // Checks if the user won or lost based on game rules
    checkResult() {
      switch (this.userItem) {
        // Scissors beats paper and lizard
        case this.items[0]:
          return (
            this.computerItem === this.items[2] ||
            this.computerItem === this.items[3]
          );
        // Spock beats scissors and rock
        case this.items[1]:
          return (
            this.computerItem === this.items[0] ||
            this.computerItem === this.items[4]
          );
        // Paper beats rock and spock
        case this.items[2]:
          return (
            this.computerItem === this.items[4] ||
            this.computerItem === this.items[1]
          );
        // Lizard beats spock and paper
        case this.items[3]:
          return (
            this.computerItem === this.items[1] ||
            this.computerItem === this.items[2]
          );
        // Rock beats lizard and scissors
        case this.items[4]:
          return (
            this.computerItem === this.items[3] ||
            this.computerItem === this.items[0]
          );
        default:
          console.log("error result");
          break;
      }
    },
  },
};
</script>

<style scoped>
.main {
  max-width: 1200px;
  margin: 0 auto;
  padding: 1rem;
}
.rules {
  box-shadow: none;
  border: 1px solid var(--headerOutline);
  background-color: transparent !important;
  padding: 0 2rem !important;
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
