<template>
  <div class="wrapper">
    <the-header></the-header>
    <main>
      <job-listings></job-listings>
    </main>
  </div>
</template>
<script>
import TheHeader from "./components/TheHeader.vue";
import JobListings from "./components/JobListings.vue";
export default {
  components: {
    TheHeader,
    JobListings,
  },
};
</script>
<style>
:root {
  --DesaturatedDarkCyan: hsl(180, 29%, 50%);
  --LightGrayishCyanBG: hsl(180, 52%, 96%);
  --LightGrayishCyanFilterTablets: hsl(180, 31%, 95%);
  --DarkGrayishCyan: hsl(180, 8%, 52%);
  --VeryDarkGrayishCyan: hsl(180, 14%, 20%);
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-color: var(--LightGrayishCyanBG);
  font-family: "Spartan", sans-serif;
  font-weight: 500;
}
main {
  margin-top: 60px;
}
</style>
