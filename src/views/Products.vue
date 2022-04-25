<template>
  <div class="container">
    <!-- <img src="" alt=""> -->
    <Header title="3D Printed" subtitle="Opening Promotion - 20% Discount" />
    <div class="container-info">
      <h2>Results : {{ totalProducts }}</h2>
      <h2>On Special: {{ totalSpecial }}</h2>
      <h2>All Products Prices: ${{ totalPrice }}</h2>
      <h2>All Products Discount: ${{ totalDiscount }}</h2>
      <button @click="toggleModal">Specials</button>
      <button @click="toggleModal2">Cart</button>
      <div v-if="modal.showModal">
        <Modal @close="toggleModal" buttonText="Sign Up Now">
          <h1>Hello dear Visitor</h1>
          <p>Welcome to DataJames/3D-Printing-Guy</p>
          <p>
            Sign-up now to view our items and get access to exclusive specials.
          </p>
          <template v-slt="links">
            <p><a href="#">Log In</a></p>
            <p><a href="#">Find Out More</a></p>
          </template>
          <!-- <Modal
          :title="modal.title"
          :text="modal.text"
          buttonText="Sign Up Now"
          @close="toggleModal"
        /> -->
        </Modal>
      </div>
      <div v-if="modal.showModal2">
        <Modal @close="toggleModal2" buttonText="Go to cart">
          <h1>Go to your cart now</h1>
          <p>Remmeber our huge specials</p>
        </Modal>
      </div>
    </div>

    <div class="page-content">
      <!-- add a for loop to loop through each category -->
      <button @click="showAll()">{{ categories[0] }}</button>
      <!-- change this to button component if possible -->
      <button @click="toggleCategory('Fan Art')">{{ categories[1] }}</button>
      <button @click="toggleCategory('History')">{{ categories[2] }}</button>
      <button @click="toggleCategory('Home')">{{ categories[3] }}</button>
      <button @click="toggleCategory('Ecology')">{{ categories[4] }}</button>
      <button @click="toggleCategory('History')">{{ categories[1] }}</button>
      <button @click="toggleCategory('Home')">{{ categories[1] }}</button>
      <button @click="toggleCategory('Ecology')">{{ categories[1] }}</button>

      <Product
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
        :addtocart="prod.addtocart"
        :id="prod.id"
      />
    </div>
  </div>
</template>

<script>
import Product from "@/components/Product.vue";
import Header from "@/components/Header.vue";
import Modal from "@/components/Modal.vue";
// import Button from "@/components/Button.vue";

export default {
  components: {
    Product,
    Header,
    Modal,
    // Button,
  },
  data() {
    return {
      categories: ["All", "Fan Art", "History", "Home", "Ecology"],
      modal: {
        showModal: false,
        showModal2: false,
      },
      products: [
        {
          pimg: require("../assets/spiderman_bust.jpeg"),
          pname: "Spiderman Bust",
          pprice: 20,
          special: true,
          sold: true,
          plink: "https://www.google.com",
          visible: true,
          category: "Fan Art",
          printtime: "11-hours",
          addtocart: 0,
          id: 1,
          // size
          // weight
          // colors
          // custom
          // time
          // category
        },
        {
          pimg: require("../assets/mandalorian_bust.png"),
          pname: "Mandalorian Bust",
          pprice: 22,
          special: true,
          sold: false,
          plink: "",
          visible: true,
          category: "Fan Art",
          addtocart: 0,
          id: 2,
        },
        {
          pimg: require("../assets/funko_pop_venom.png"),
          pname: "Funko Pop Venom",
          pprice: 15,
          special: true,
          sold: false,
          plink: "",
          visible: true,
          category: "Fan Art",
          addtocart: 0,
          id: 3,
        },
        {
          pimg: require("../assets/funko_pop_venom.png"),
          pname: "Venom Figurine",
          pprice: 5,
          special: true,
          sold: false,
          plink: "",
          visible: true,
          category: "Fan Art",
          addtocart: 0,
          id: 4,
        },
        {
          pimg: require("../assets/baby_yoda.jpeg"),
          pname: "Baby Yoda",
          pprice: 10,
          special: true,
          sold: false,
          plink: "",
          visible: true,
          category: "Fan Art",
          addtocart: 0,
          id: 5,
        },
        {
          pimg: require("../assets/raptor_claw.png"),
          pname: "Raptor Claw",
          pprice: 4,
          special: true,
          sold: false,
          plink: "",
          visible: true,
          category: "History",
          addtocart: 0,
          id: 6,
        },
        {
          pimg: require("../assets/thor_hammer_pen.png"),
          pname: "Thor Hammer Pen",
          pprice: 10,
          special: true,
          sold: false,
          plink: "",
          visible: true,
          category: "Fan Art",
          addtocart: 0,
          id: 7,
        },
        {
          pimg: require("../assets/bonsai_planter.png"),
          pname: "Bonsai Planter",
          pprice: 4,
          special: true,
          sold: false,
          plink: "",
          visible: true,
          category: "Ecology",
          addtocart: 0,
          id: 8,
        },
        {
          pimg: require("../assets/self-watering_planter.png"),
          pname: "Self-Watering Planter",
          pprice: 4,
          special: true,
          sold: false,
          plink: "",
          visible: true,
          category: "Ecology",
          addtocart: 0,
          id: 9,
        },
        {
          pimg: require("../assets/spiderman_bust.jpeg"),
          pname: "Spiderman Bust",
          pprice: 20,
          special: true,
          sold: false,
          plink: "https://www.google.com",
          visible: true,
          category: "Fan Art",
          printtime: "11-hours",
          addtocart: 0,
          id: 10,
          // size
          // weight
          // colors
          // custom
          // time
          // category
        },
      ],
    };
  },
  computed: {
    // return {
    totalProducts: function () {
      return this.products.length;
    },
    totalSpecial: function () {
      return this.products.filter(function (product) {
        return product.special;
      }).length;
    },
    totalPrice: function () {
      return this.products.reduce(function (total, product) {
        return total + product.pprice;
      }, 0);
    },
    totalDiscount: function () {
      return this.products.reduce(function (total, product) {
        if (product.special) {
          return total + product.pprice * 0.2;
        } else {
          return total + product.pprice;
        }
      }, 0);
    },
  },
  methods: {
    toggleCategory(cat) {
      // this function hides and displays items based on categories clicked
      return this.products.filter(function (product) {
        if (product.category !== cat) {
          return (product.visible = false);
        } else if (product.category === cat) {
          return (product.visible = true);
        }
      });
      // console.log("hello");
    },
    showAll() {
      // this function hides and displays all items
      return this.products.filter(function (product) {
        if (product.visible === false) {
          return (product.visible = true);
        }
      });
    },
    toggleModal() {
      // this function toggles the modal
      this.modal.showModal = !this.modal.showModal;
    },
    toggleModal2() {
      // this function toggles the modal2
      this.modal.showModal2 = !this.modal.showModal2;
    },
  },
};
</script>
<style>
.page-content {
  display: grid;
  flex-wrap: wrap;
  overflow: auto;
  grid-gap: 1rem;
  padding: 1rem;
  max-width: 1024px;
  margin: 0 auto;
  font-family: var(--font-sans);
}
@media (min-width: 600px) {
  .page-content {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media (min-width: 800px) {
  .page-content {
    grid-template-columns: repeat(4, 1fr);
  }
}
.active {
  border: 2px solid blue;
}
.card {
  position: relative;
  display: flex;
  align-items: flex-end;
  overflow: hidden;
  padding: 1rem;
  text-align: center;
  color: whitesmoke;
  background-color: whitesmoke;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1), 0 2px 2px rgba(0, 0, 0, 0.1),
    0 4px 4px rgba(0, 0, 0, 0.1), 0 8px 8px rgba(0, 0, 0, 0.1),
    0 16px 16px rgba(0, 0, 0, 0.1);
}
@media (min-width: 600px) {
  .card {
    height: 350px;
  }
}
.card:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 110%;
  background-size: cover;
  background-position: 0 0;
  transition: transform calc(var(--d) * 1.5) var(--e);
  pointer-events: none;
}
.card:after {
  content: "";
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 200%;
  pointer-events: none;
  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0) 0%,
    rgba(0, 0, 0, 0.009) 11.7%,
    rgba(0, 0, 0, 0.034) 22.1%,
    rgba(0, 0, 0, 0.072) 31.2%,
    rgba(0, 0, 0, 0.123) 39.4%,
    rgba(0, 0, 0, 0.182) 46.6%,
    rgba(0, 0, 0, 0.249) 53.1%,
    rgba(0, 0, 0, 0.32) 58.9%,
    rgba(0, 0, 0, 0.394) 64.3%,
    rgba(0, 0, 0, 0.468) 69.3%,
    rgba(0, 0, 0, 0.54) 74.1%,
    rgba(0, 0, 0, 0.607) 78.8%,
    rgba(0, 0, 0, 0.668) 83.6%,
    rgba(0, 0, 0, 0.721) 88.7%,
    rgba(0, 0, 0, 0.762) 94.1%,
    rgba(0, 0, 0, 0.79) 100%
  );
  transform: translateY(-50%);
  transition: transform calc(var(--d) * 2) var(--e);
}

.btn {
  cursor: pointer;
  margin-top: 1.5rem;
  padding: 0.75rem 1.5rem;
  font-size: 0.65rem;
  font-weight: bold;
  letter-spacing: 0.025rem;
  text-transform: uppercase;
  color: white;
  background-color: black;
  border: none;
}
.btn:hover {
  background-color: #0d0d0d;
}
.btn:focus {
  outline: 1px dashed yellow;
  outline-offset: 3px;
}
@media (hover: hover) and (min-width: 600px) {
  .card:after {
    transform: translateY(0);
  }
  .content {
    transform: translateY(calc(100% - 4.5rem));
  }
  .content > *:not(.title) {
    opacity: 0;
    transform: translateY(1rem);
    transition: transform var(--d) var(--e), opacity var(--d) var(--e);
  }
  .card:hover,
  .card:focus-within {
    align-items: center;
  }
  .card:hover:before,
  .card:focus-within:before {
    transform: translateY(-4%);
  }
  .card:hover:after,
  .card:focus-within:after {
    transform: translateY(-50%);
  }
  .card:hover .content,
  .card:focus-within .content {
    transform: translateY(0);
  }
  .card:hover .content > *:not(.title),
  .card:focus-within .content > *:not(.title) {
    opacity: 1;
    transform: translateY(0);
    transition-delay: calc(var(--d) / 8);
  }
  .card:focus-within:before,
  .card:focus-within:after,
  .card:focus-within .content,
  .card:focus-within .content > *:not(.title) {
    transition-duration: 0s;
  }
}
</style>
