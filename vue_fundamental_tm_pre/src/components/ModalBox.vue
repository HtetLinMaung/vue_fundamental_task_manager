<template>
  <div ref="myModal" v-show="value" class="modal">
    <div class="modal-content" :style="{ 'max-width': `${maxWidth || 250}px` }">
      <slot name="title">
        <div class="d-flex">
          <div style="font-size: 24px;">Want to code with Htet Lin Maung?</div>
          <div class="close" @click="updateFlag">&times;</div>
        </div>
        <hr />
      </slot>
      <slot name="content">
        <div>
          Let Htet Lin Maung help upgrade your coding skills. If you want to
          join please click subscribe button below.
        </div>
      </slot>
      <slot name="action">
        <hr />
        <div class="d-flex">
          <div>
            <btn>Cancel</btn>
          </div>
          <div>
            <btn>Subscribe</btn>
          </div>
        </div>
      </slot>
    </div>
  </div>
</template>

<script>
import Button from '../components/Button'

export default {
  name: 'ModalBox',
  props: ['value', 'maxWidth'],
  components: {
    btn: Button
  },
  data() {
    return {}
  },
  methods: {
    updateFlag() {
      this.$emit('input', false)
    }
  },
  mounted() {
    window.onclick = event => {
      if (event.target == this.$refs.myModal) {
        this.$emit('input', false)
      }
    }
  }
}
</script>

<style scoped>
.modal {
  display: flex;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.4);
}

.modal-content {
  background-color: #fefefe;
  margin: auto;
  padding: 20px;
  border: 1px solid #888;
  border-radius: 4px;
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

.d-flex {
  display: flex;
  align-items: flex-start;
}
</style>
