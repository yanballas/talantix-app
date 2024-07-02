<template>
  <div class="modal" v-if="showModal" @click="hideModal">
    <div @click.stop class="modal--wrapper">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    showModal: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    hideModal() {
      this.$emit("update:showModal", false);
    },
  },
};
</script>

<style scoped>
.modal {
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal--wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  background: #fff;
  border-radius: 8px;
  height: 60vh;
  width: 60vw;
  padding: 32px;
}
</style>
