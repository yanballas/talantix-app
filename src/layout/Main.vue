<template>
  <main class="main">
    <table v-if="isItemsLoading" class="table">
      <thead class="table--header">
        <tr class="table--line">
          <th
            class="table--cell table--filtered"
            @click="handleSortValue('company')"
          >
            Название &#11015;
          </th>
          <th
            class="table--cell table--filtered table--stroke"
            @click="handleSortValue('name')"
          >
            ФИО директора &#11015;
          </th>
          <th class="table--cell table--stroke">Номер телефона</th>
          <th class="table--cell"></th>
        </tr>
      </thead>
      <Items :items="items" @remove="handleRemove"></Items>
    </table>
    <div v-else class="main--preloader">
      <h2 class="main--headling">Идёт загрузка</h2>
    </div>
  </main>
</template>

<script>
import Items from "../components/Items.vue";
export default {
  components: {
    Items,
  },
  props: {
    items: {
      type: Array,
      required: true,
    },
    isItemsLoading: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    handleRemove(item) {
      this.$emit("remove", item);
    },
    handleSortValue(value) {
      this.$emit("sort", value);
    },
  },
};
</script>

<style>
.main {
  flex-grow: 1;
}

.main--preloader {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.main--headling {
  font-size: 32px;
  line-height: 120%;
}

.table {
  border: 2px solid #008c8c;
  width: 100%;
  font-size: 16px;
  line-height: 120%;
  text-align: left;
}

.table--header,
.table--cell {
  padding: 12px;
  border-bottom: 2px solid #008c8c;
}

.table--body .table--line:hover {
  background-color: #cbd6cb;
}

.table--header {
  background-color: #c6cfbf;
}

.table--filtered:hover {
  cursor: pointer;
  background-color: #a9c1a8;
}

.table--stroke {
  border-left: 2px solid #008c8c;
  border-right: 2px solid #008c8c;
}

.table--cell:last-child {
  text-align: center;
}
</style>
