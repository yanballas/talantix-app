<template>
  <div class="pagination">
    <Button @click="prevPage" :disabled="currentPage === 1">&larr;</Button>
    <p>Страница {{ currentPage }}</p>
    <Button @click="nextPage" :disabled="currentPage === pages">&rarr;</Button>
  </div>
</template>

<script>
import Button from "./Button.vue";
export default {
  components: {
    Button,
  },
  props: {
    currentPage: {
      type: Number,
      required: true,
    },
    pages: {
      type: Number,
      default: true,
    },
  },

  methods: {
    prevPage() {
      if (this.currentPage > 1) {
        this.$emit("update:page", this.currentPage - 1);
      }
    },
    nextPage() {
      if (this.currentPage < this.pages) {
        this.$emit("update:page", this.currentPage + 1);
      }
    },
  },
};
</script>

<style scoped>
.pagination {
  font-size: 18px;
  line-height: 140%;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 16px;
}
</style>
