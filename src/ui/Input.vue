<template>
  <input
    class="input"
    :type="type"
    :placeholder="placeholder"
    :value="modelValue"
    @input="updateInput"
  />
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: "text",
    },
    placeholder: {
      type: String,
      default: "",
    },
    modelValue: [String, Number],
  },
  methods: {
    updateInput(e) {
      this.$emit("update:modelValue", e.target.value);
    },
  },
};
</script>

<style scoped>
.input {
  padding: 8px;
  font-size: 14px;
  border: 2px solid #008c8c;

  &:focus,
  &:focus-visible {
    outline: none;
    background: #cbd6cb;
  }
}
</style>
