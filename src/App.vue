<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>Todoリスト</h1>
    <hr />
    <div>
      {{ msg }}
      <form>
        <button>追加</button>
        <button>完了を削除</button>
        <p>入力: <input type="text"></p>
        <p>タスク:</p>
      </form>
      <div class="task-list">
        <label class="task-list__item"><input type="checkbox"><button>編集</button>vue-router</label>
        <label class="task-list__item"><input type="checkbox"><button>編集</button>vuex</label>
        <label class="task-list__item"><input type="checkbox"><button>編集</button>vue-loader</label>
        <label class="task-list__item--checked"><input type="checkbox" checked><button>編集</button>awesome-vue</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
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
