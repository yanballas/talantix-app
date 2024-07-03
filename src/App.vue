<template>
  <div class="app">
    <Header
      v-model:showModal="modalOpacity"
      v-model:searchItem="searchValue"
    ></Header>
    <Main
      :isItemsLoading="isItemsLoading"
      :items="filterBySearchItems"
      @remove="deleteItem"
      @sort="currentSortValue"
    ></Main>
    <Pagination
      :pages="maxPages"
      :currentPage="currentPage"
      v-model:page="currentPage"
    ></Pagination>
    <Modal v-model:showModal="modalOpacity">
      <Form
        v-model:showModal="modalOpacity"
        :items="items"
        @create="createItem"
        class="modal--form"
      ></Form>
    </Modal>
  </div>
</template>

<script>
import Header from "./layout/Header.vue";
import Main from "./layout/Main.vue";
import Pagination from "./ui/Pagination.vue";
import Modal from "./ui/Modal.vue";
import Form from "./components/Form.vue";

export default {
  components: {
    Header,
    Main,
    Pagination,
    Modal,
    Form,
  },
  data() {
    return {
      items: [],
      sortValue: "",
      searchValue: "",
      currentPage: 1,
      maxItems: 5,
      maxPages: 2,
      modalOpacity: false,
      isItemsLoading: false,
    };
  },
  methods: {
    createItem(item) {
      this.items.push(item);
    },
    deleteItem(item) {
      this.items = this.items.filter((value) => value.id !== item.id);
    },
    async getItems() {
      try {
        const response = await fetch(
          `https://jsonplaceholder.typicode.com/users?_limit=${this.maxItems}&_page=${this.currentPage}`
        );

        if (response.ok) {
          const data = await response.json();
          this.isItemsLoading = true;
          const newData = data.map((el) => ({
            id: el.id,
            name: el.name,
            phone: el.phone,
            company: el.company.name,
          }));
          this.items = newData;
        } else {
          console.log("Response not ok:", response);
        }
      } catch (error) {
        console.log("Fetch error:", error);
      }
    },
    compareItem(a, b) {
      if (a < b) return -1;

      if (a > b) return 1;

      return 0;
    },
    currentSortValue(value) {
      this.sortValue = value;
    },
  },
  mounted() {
    this.getItems();
  },
  computed: {
    sortItems() {
      return [...this.items].sort((a, b) =>
        this.compareItem(a[this.sortValue], b[this.sortValue])
      );
    },
    filterBySearchItems() {
      return this.sortItems.filter((item) =>
        item.name.toLowerCase().includes(this.searchValue.toLowerCase())
      );
    },
  },
  watch: {
    currentPage() {
      this.getItems();
    },
  },
};
</script>

<style scoped>
.app {
  display: flex;
  flex-direction: column;
  gap: 48px;
  justify-content: space-between;
  width: 90vw;
  height: 90vh;
}

.modal--form {
  width: 100%;
}
</style>
