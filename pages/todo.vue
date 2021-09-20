<template>
  <div id="app">
    <div class="content">
      <div class="todo">
        <input type="text" class="memo" placeholder="ここにやることを入力しよう！">
        <input type="button" @click="fetchSomething" value="追加！">
      </div>
      <div class="list">
        ここにチェックボックスを表示する
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      data:''
    }
  },
  methods: {
    async fetchSomething() {
      this.data = JSON.stringify(await this.$axios.$get('http://127.0.0.1:8000/api/test'))
    }
  }
}
</script>

<style>
.content {
    padding: 20px;
    text-align: center;
    background-color: azure;
    margin: 30px 300px;
}
.memo {
    width: 500px;
}
</style>
