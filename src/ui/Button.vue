<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {};
</script>

<style scope>
.btn {
  cursor: pointer;
  background: #fff;
  border: 2px solid #008c8c;
  border-radius: 8px;
  font-size: 16px;
  line-height: 140%;
}
</style>
