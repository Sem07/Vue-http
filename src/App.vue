<template>
  <div class="center">
    <input type="text" v-model="text" />
    <button @click="addTodolist" v-show="actions.length < 10">
      Add new todo
    </button>

    <ul>
      <li v-for="(action, i) in actions" :key="`${i} - ${action}`">
        {{ action }}
        <button @click="remove(i)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      text: "",
      actions: ["Go to the shop", "Go for a walk", "Make a coffe"],
      delet: true,
    };
  },
  methods: {
    addTodolist() {
      this.$http.post(
        "https://todolist-49942.firebaseio.com/todolist.json",
        this.text
      );
      console.log(this.text);
    },
    remove(i) {
      this.actions.splice(i, 1);
    },
  },
};
</script>

<style>
.center {
  text-align: center;
}
</style>
