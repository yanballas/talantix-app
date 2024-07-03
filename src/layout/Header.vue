<template>
  <header class="header">
    <Input
      v-model.trim="searchFilterValue"
      type="text"
      placeholder="Найти по ФИО..."
    ></Input>
    <Button @click="openModal">Добавить</Button>
  </header>
</template>

<script>
import Button from "../ui/Button.vue";
import Input from "../ui/Input.vue";
export default {
  components: {
    Button,
    Input,
  },
  data() {
    return {
      searchFilterValue: "",
    };
  },
  methods: {
    openModal() {
      this.$emit("update:showModal", true);
    },
  },
  watch: {
    searchFilterValue(value) {
      this.$emit("update:searchItem", value);
    },
  },
};
</script>

<style scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
