<template>
  <div class="card">
    <h3 class="headling">Добавить организацию</h3>
    <form class="card--form" @submit.prevent>
      <Input
        v-model="item.title"
        type="text"
        placeholder="Название"
      />
      <Input
        v-model="item.number"
        type="text"
        placeholder="Номер телефона"
      />
      <Input
        v-model="item.name"
        type="text"
        placeholder="ФИО директора"
      />
    </form>
    <div class="card--btns">
      <Button>Отмена</Button>
      <Button @click="addItem">Ок</Button>
    </div>
  </div>
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
      item: {
        title: "",
        name: "",
        number: "",
      },
    };
  },
  methods: {
    addItem() {
      this.item.id = Date.now();
      this.$emit("create", this.item);
      this.clearItem();
    },
    clearItem() {
      this.title = "";
      this.name = "";
      this.number = "";
    },
  },
};
</script>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  gap: 12px;
  border: 2px solid #008c8c;
}

.headling {
  padding: 16px;
  font-size: 18px;
  font-weight: 700;
  border-bottom: 2px solid #008c8c;
}

.card--form {
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 16px;
  border-bottom: 2px solid #008c8c;
}

.card--btns {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 24px;
  padding: 16px;
}
</style>
