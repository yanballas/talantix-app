<template>
  <tr class="table--line">
    <td class="table--cell">{{ item.company }}</td>
    <td class="table--cell table--stroke">{{ item.name }}</td>
    <td class="table--cell table--stroke">{{ item.phone }}</td>
    <td
      class="table--cell table--delete"
      @click="$emit('remove', item)"
      v-if="showDeleteBtn"
    >
      &#10062;
    </td>
    <td v-else class="table--cell"></td>
  </tr>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
    showDeleteBtn: {
      type: Boolean,
      default: true,
    },
  },
};
</script>

<style scoped>
.table--delete {
  cursor: pointer;
}
</style>
