<template>
  <div class="">
    <header>
      <h1>{{ title }}</h1>
      <h3>{{ subtitle }}</h3>
      <div>
        <Button text="Previous" color="red" />
        <Button text="Next" color="green" />
        <button @click="goBack">Go Back</button>
      </div>
    </header>
  </div>
</template>

<script>
import Button from "./Button.vue";

export default {
  name: "Header",
  props: ["title", "subtitle", "text"],
  components: {
    Button,
  },
  methods: {
    redirect() {
      this.$router.push("/");
    },
    goBack() {
      this.$router.go(-1);
    },
    goForward() {
      this.$router.go(1);
    },
  },
};
</script>

<style scoped>
header {
  margin-bottom: 20px;
  text-align: center;
  margin: 20px;
}
</style>
