<template>
  <v-app class="body">
    <v-main>
      <Nuxt />
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import Footer from "./footer.vue";

export default {
  name: "DefaultLayout",
  components: {
    Footer,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@400;600;700&display=swap");

:root {
  --footerText: hsl(227, 36%, 57%);
  --darkText: hsl(229, 25%, 31%);
  --scoreText: hsl(229, 64%, 46%);
  --headerOutline: hsl(217, 16%, 45%);
}

.body {
  background: radial-gradient(
    hsl(214, 47%, 23%),
    hsl(237, 49%, 15%)
  ) !important;
  font-family: "Barlow Semi Condensed";
  font-weight: 600;
}
</style>
