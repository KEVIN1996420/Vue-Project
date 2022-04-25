<template>
  <div id="app">
    <div id="nav">
      <router-link to="/home">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/products">3D Prints</router-link> |
      <router-link to="/custom">Custom</router-link> |
      <router-link to="/contact">Contact</router-link> |
      <input type="text" placeholder="Search.." ref="searchBar" value="dsknv" />
      <Button class="searchBtn" @click="btnClick" text="search"></Button>
    </div>
    <router-view />
    <!-- component for the route will be mounted here -->
  </div>
</template>

<script>
import Button from "./components/Button.vue";

export default {
  components: {
    Button,
  },
  methods: {
    btnClick() {
      // save the value in searchbar
      const searchValue = this.$refs.searchBar.value;
      console.log(searchValue);
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

input[type="text"] {
  /* float: right; */
  padding: 6px;
  border: 1px solid black;
  /* margin-top: 8px; */
  /* margin-right: 16px; */
  font-size: 17px;
}
.container {
  max-width: 90vw;
  margin: 30px auto;
  overflow: auto;
  /* border: 1px solid blue; */
  border-radius: 5px;
  padding: 30px;
}
.btn {
  display: inline-block;
  /* background-color: #42b983; */
  border: 1px solid green;
  padding: 15px;
  color: white;
  border-radius: 5px;
  font-weight: bold;
}
</style>
