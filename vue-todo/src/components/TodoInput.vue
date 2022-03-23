<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" />
    <!-- input 에 입력된 값을 동적으로 vue 인스턴스에 매핑하는 역할 -->
    <!-- <button v-on:click="appTodo">add</button> -->
    <span class="addContainer" v-on:click="addTodo">
      <i class="fa-solid fa-plus addBtn"></i>
    </span>
    <!-- use the modal component, pass in the prop -->
    <Modal v-if="showModal" @close="showModal = false">
      <!--
      you can use custom content here to overwrite
      default content
    -->
      <h3 slot="header">
        경고!<i
          class="fas fa-times closeModalBtn"
          @click="showModal = false"
        ></i>
      </h3>
      <p slot="body">아무것도 입력하지 않으셨습니다.</p>
      <p slot="footer">copy right</p>
    </Modal>
  </div>
</template>

<script>
import Modal from "./common/Modal.vue";
export default {
  data() {
    return {
      newTodoItem: "",
      showModal: false,
    };
  },
  methods: {
    addTodo() {
      if (this.newTodoItem !== "") {
        // var obj = { completed: false, item: this.newTodoItem };
        // localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
        // this.$emit('이벤트 이름', 인자1, 인자2, ...);
        // this.$emit("addTodoItem", this.newTodoItem);
        const text = this.newTodoItem.trim();
        this.$store.commit("addOneItem", text);
        this.cliearInput();
      } else {
        // alert("왜 아무것도 안쳐");
        this.showModal = !this.showModal;
      }
    },
    cliearInput() {
      this.newTodoItem = "";
    },
  },
  components: {
    Modal,
  },
};
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
.closeModalBtn {
  color: #42b983;
}
</style>