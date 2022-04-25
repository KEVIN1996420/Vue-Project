<template>
  <div class="container">
    <!-- <img src="" alt=""> -->
    <Header
      title="Custom Designs"
      subtitle="Opening Promotion - 10% Discount"
    />
    <div class="page-content">
      <!-- <Product
        class="card"
        v-for="(prod, i) in products"
        :key="i"
        :index="i + 1"
        :pimg="prod.pimg"
        :pname="prod.pname"
        :pprice="prod.pprice"
        :special="prod.special"
        :sold="prod.sold"
        :plink="prod.plink"
        :visible="prod.visible"
        :category="prod.category"
        :printtime="prod.printtime"
      /> -->
    </div>
  </div>
</template>
<script>
// import Product from "@/components/Product.vue";
import Header from "@/components/Header.vue";

export default {
  data() {
    return {
      // how to import data from other Products View
      category: "",
    };
  },
  computed: {},
  components: {
    // Product,
    Header,
  },
};
</script>