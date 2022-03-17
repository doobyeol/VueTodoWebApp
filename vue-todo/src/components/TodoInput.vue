<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="appTodo" />
    <!-- input 에 입력된 값을 동적으로 vue 인스턴스에 매핑하는 역할 -->
    <!-- <button v-on:click="appTodo">add</button> -->
    <span class="addContainer" v-on:click="appTodo">
      <i class="fa-solid fa-plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      newTodoItem: "",
    };
  },
  methods: {
    appTodo: function () {
      if (this.newTodoItem !== "") {
        var obj = { completed: false, item: this.newTodoItem };
        //console.log(this.newTodoItem);
        // 저장하는 로직
        // localStorage.setItem(this.newTodoItem, obj);
        localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
        this.cliearInput();
      }
    },
    // 메소드 분할
    cliearInput: function () {
      this.newTodoItem = "";
    },
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