<script>
import Header from "./layout/Header.vue";
import Main from "./layout/Main.vue";
import Modal from "./ui/Modal.vue";
import Form from "./components/Form.vue";

export default {
  components: {
    Header,
    Main,
    Modal,
    Form,
  },
  data() {
    return {
      modalOpacity: false,
    };
  },
};
</script>

<template>
  <div class="app">
    <Header v-model:showModal="modalOpacity"></Header>
    <Main></Main>
    <Modal v-model:showModal="modalOpacity">
      <Form @create="createItem" class="modal--form"></Form>
    </Modal>
  </div>
</template>

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
