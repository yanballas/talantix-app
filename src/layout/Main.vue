<template>
  <main class="main">
    <table class="table">
      <thead class="table--header">
        <tr class="table--line">
          <th class="table--cell table--filtered">Название &#11015;</th>
          <th class="table--cell table--filtered table--stroke">
            ФИО директора &#11015;
          </th>
          <th class="table--cell table--stroke">Номер телефона</th>
          <th class="table--cell"></th>
        </tr>
      </thead>
      <Items :items="items" @remove="deleteItem"></Items>
    </table>
  </main>
</template>

<script>
import Items from "../components/Items.vue";
export default {
  components: {
    Items,
  },
  data() {
    return {
      items: [
        {
          id: 1,
          title: 'ООО "Вектор"',
          name: "Иванов И.И.",
          number: "7999999999",
        },
        {
          id: 2,
          title: "ИП Сидоров С.С.",
          name: "Сидоров С.С.",
          number: "7546456456456",
        },
      ],
    };
  },
  methods: {
    createItem(item) {
      this.items.push(item);
    },
    deleteItem(item) {
      this.items = this.items.filter((value) => value.id !== item.id);
    },
  },
};
</script>

<style>
.main {
  flex-grow: 1;
  border: 2px solid #008c8c;
}

.table {
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
