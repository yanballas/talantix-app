<template>
  <header class="header">
    <p>header</p>
    <Button @click="openModal">Добавить</Button>
  </header>
</template>

<script>
import Button from "../ui/Button.vue";
export default {
  components: {
    Button,
  },
  methods: {
    openModal() {
      this.$emit("update:showModal", true);
    },
  },
};
</script>

<style scoped>
.header {
  padding: 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
