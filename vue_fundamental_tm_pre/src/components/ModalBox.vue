<template>
  <div ref="myModal" v-show="value" class="modal">
    <div class="modal-content">
      <div class="d-flex">
        <div class="close" @click="updateFlag">&times;</div>
      </div>
      <slot name="content"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalBox",
  props: ["value"],
  data() {
    return {};
  },
  methods: {
    updateFlag() {
      this.$emit("input", false);
    }
  },
  mounted() {
    window.onclick = event => {
      if (event.target == this.$refs.myModal) {
        this.$emit("input", false);
      }
    };
  }
};
</script>

<style scoped>
.modal {
  display: block;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.4);
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}

.close {
  color: #aaa;
  margin-left: auto;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
</style>
