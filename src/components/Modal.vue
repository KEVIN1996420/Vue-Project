<template>
  <div id="modalDiv" class="backdrop" @click.self="closeModal">
    <div class="modal">
      <slot></slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
      <!-- for using props --><!-- <h1>{{ title }}</h1> --><!-- <p>{{ text }}</p> -->
      <Button :text="buttonText">{{ buttonText }}</Button>
    </div>
  </div>
</template>

<script>
import Button from "@/components/Button.vue";

export default {
  props: ["buttonText"], // "title", "text",
  components: {
    Button,
  },
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>
<style>
#modalDiv {
  display: visible;
}
.modal {
  width: 50%;
  margin: auto;
  background-color: white;
  border-radius: 10px;
  top: 25%;
  left: 25%;
  position: fixed;
  padding: 20px;
}
.backdrop {
  top: 0;
  left: 0;
  position: absolute;
  z-index: 2;
  background-color: rgba(0, 0, 0, 0.363);
  width: 100%;
  height: 100%;
  /* padding: 20px; */
}
h1 {
  color: rgb(42, 87, 95);
}
.actions {
  display: flex;
  justify-content: flex-end;
  text-align: center;
}
</style>
