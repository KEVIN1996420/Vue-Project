<template>
  <div
    class="card"
    v-if="visible"
    :style="{
      backgroundImage: `url(${pimg})`,
      backgroundPosition: 'center',
      backgroundSize: 'cover',
    }"
  >
    <!-- :class="[visible ? 'visible' : 'hidden']" -->
    <div class="content">
      <h1 class="title">{{ pname }}</h1>
      <!--  :class="[{ 'bg-sold': sold }, prodName]" -->
      <!-- <p>Product Number : {{ index }}</p> -->
      <p class="copy">Discount: ${{ priceDiscount }}</p>
      <p class="copy">{{ category }}</p>
      <p class="copy">{{ printtime }}</p>
      <p class="copy">{{ addtocart }}</p>
      <router-link
        :to="{
          name: 'ProductDetails',
          params: {
            id,
            pname,
            pprice,
            special,
            sold,
            category,
            printtime,
          },
        }"
      >
        <h2>View</h2>
      </router-link>
      <!-- <button class="btn" @click="addtocart++">Add</button> -->
      <!-- <button class="btn" @click="addtocart--">Remove</button> -->
    </div>
  </div>
</template>

<script>
export default {
  props: [
    "pimg",
    "pname",
    "pprice",
    "special",
    "sold",
    "index",
    "plink",
    "visible",
    "category",
    "printtime",
    "addtocart",
    "id",
  ],
  computed: {
    // prodName() {
    //   if (this.sold === false) {
    //     return "blue";
    //   } else {
    //     return "red  "; //default if no match
    //   }
    // },
    priceDiscount() {
      if (this.special === true) {
        return this.pprice * 0.2;
      } else {
        return this.pprice;
      }
    },
  },
};
</script>

<style>
a {
  cursor: pointer;
  text-decoration: none;
}

img {
  max-width: 50px;
  max-height: 50px;
}
.hidden {
  display: none;
}
.visible {
  display: block;
}
.bg-sold {
  background-color: red;
}
.red {
  color: red;
}
.blue {
  color: blue;
}

.content {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  padding: 1rem;
  transition: transform var(--d) var(--e);
  z-index: 1;
}
.content > * + * {
  margin-top: 1rem;
}
.title {
  font-size: 1.3rem;
  font-weight: bold;
  line-height: 1.2;
}
.copy {
  font-family: var(--font-serif);
  font-size: 1.125rem;
  font-style: italic;
  line-height: 1.35;
}
</style>
