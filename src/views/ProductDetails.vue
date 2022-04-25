<template>
  <div class="container">
    <Header
      title="Product Details"
      subtitle="Find out more about this product before purchasing."
    />
    <p>
      {{ id }} - {{ pname }} - {{ pprice }} - {{ special }} - {{ sold }} -
      {{ category }} - {{ printtime }} - {{ addtocart }}
    </p>
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
// import Product from "@/components/Product.vue";

export default {
  name: "ProductDetails",
  components: {
    Header,
    // Product,
  },
  props: [
    "id",
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
  ],
  // data() {
  //   return {
  //     id: this.$route.params.id, // get the param from the url
  //   };
  // },
};
</script>