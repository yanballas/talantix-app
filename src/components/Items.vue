<template>
  <tbody class="table--body" v-if="items.length > 0">
    <Item
      v-for="item in items"
      :item="item"
      :key="item.id"
      @remove="$emit('remove', item)"
    ></Item>
  </tbody>
  <tbody v-else class="table--body">
    <Item
      :item="{ company: 'Нет данных', name: 'Нет данных', phone: 'Нет данных' }"
      :showDeleteBtn="false"
    />
  </tbody>
</template>

<script>
import Item from "./Item.vue";
export default {
  components: {
    Item,
  },
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.table--headling {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
