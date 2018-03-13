<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>Todoリスト</h1>
    <hr />
    <div>
      {{ msg }}
      <form>
        <button @click="addTodo">追加</button>
        <button @click="removeTodo">完了を削除</button>
        <p>入力: <input type="text" v-model="newTodo"></p>
        <p>タスク: {{ newTodo }}</p>
      </form>
      <div class="task-list">
        <label class="task-list__item"
               v-for="todo in todos"
               v-bind:class="{ 'task-list__item--checked': todo.done }">
          <input type="checkbox" v-model="todo.done">
          <input type="checkbox" v-model="todo.editing">
          <input v-if="todo.editing" v-model="todo.text" @keyup.enter="todo.editing = !todo.editing">
          <span v-else>{{ todo.text }}</span>
        </label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      todos: [
        { text: 'vue-router', done: false, editing:false },
        { text: 'vuex', done: false, editing:false },
        { text: 'vue-loader', done: false, editing:false },
        { text: 'awesome-vue', done: true, editing:false }
      ],
      newTodo: ""
    }
  },
  methods: {
    addTodo (event) {
      event.preventDefault();
      let text = this.newTodo && this.newTodo.trim()
      if (!text) {
        return
      }
      this.todos.push({
        text,
        done: false
      })
      this.newTodo = '';
    },
    removeTodo (event) {
      event.preventDefault();
      for (let i = this.todos.length - 1; i >= 0; i--) {
        if (this.todos[i].done) this.todos.splice(i, 1);
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.task-list {
  display: flex;
  display: -webkit-flex;
  display: -moz-flex;
  display: -ms-flex;
  display: -o-flex;
  flex-direction: column;
  align-items: center;
}

.task-list__item {
  width: 270px;
  text-align: left;
}

.task-list__item--checked {
  width: 270px;
  text-align: left;
  color: #85a6c6;
}

</style>
