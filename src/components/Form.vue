<template>
  <div class="card">
    <h3 class="headling">Добавить организацию</h3>
    <form class="card--form" @submit.prevent>
      <Input v-model.trim="item.company" type="text" placeholder="Название" />
      <Input
        v-model.trim="item.phone"
        type="number"
        placeholder="Номер телефона"
      />
      <Input v-model.trim="item.name" type="text" placeholder="ФИО директора" />
    </form>
    <div class="card--btns">
      <Button @click="clearItem" class="card--btn_clean">Стереть</Button>
      <Button @click="hideModal">Отмена</Button>
      <Button :disabled="!isFormValid" @click="handleSuccessClick">Ок</Button>
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
  props: {
    items: {
      type: Array,
    },
  },
  data() {
    return {
      item: {
        company: "",
        name: "",
        phone: "",
      },
    };
  },
  computed: {
    isFormValid() {
      for (let key in this.item) {
        if (this.item[key] === "") {
          return false;
        }
      }
      return true;
    },
  },
  methods: {
    addItem() {
      if (this.isFormValid) {
        const id = this.items.reduce((acc, val) => {
          if (val.id > acc) return (acc = val.id);
          return acc;
        }, 0);

        this.item.id = id + 1;
        this.$emit("create", this.item);
      }
    },
    clearItem() {
      this.item.company = "";
      this.item.name = "";
      this.item.phone = "";
    },
    hideModal() {
      this.$emit("update:showModal", false);
    },
    handleSuccessClick() {
      this.addItem();
      this.hideModal();
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
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
  padding: 16px;
}

.card--btn_clean {
  grid-column: 1 / -1;
}
</style>
