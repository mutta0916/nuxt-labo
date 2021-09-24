<template>
  <div id="app">
    <div class="content">
      <div class="todo">
        <input type="text" class="input" placeholder="ここにやることを入力しよう！" v-model="input">
        <input type="button" @click="addData" value="追加！">
        <table>
          <tr v-for="(row, index) in data" :key="index">
            <td>{{row}}</td>
            <input v-if="data.length > 0" type="button" @click="modData" value="変更！">
            <input v-if="data.length > 0" type="button" @click="delData" value="削除！">
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      input:'',
      data: []
    }
  },
  methods: {
    async fetchSomething() {
      this.data = JSON.stringify(await this.$axios.$get('http://127.0.0.1:8000/api/test'));
    },
    addData: function() {
      this.data.push(this.input);
      this.input = '';
    },
    modData: function() {
      this.data.push(this.input);
      this.input = '';
    },
    delData: function() {
      this.data.splice(this.data.indeOf());
      this.input = '';
    }
  }
}
</script>

<style>
.content {
  background-color:#E79460;
  margin: 0 auto;
  margin-top: 50px;
}

.todo {
  text-align: center;
  padding: 20px 40px;
  border: 1px solid black;
}
/* .content {
    padding: 20px; */
    /* text-align: center; */
    /* background-color: azure; */
    /* margin: 30px 300px; */
    /* margin: 0 auto;
}
.memo {
    width: 500px;
} */
</style>
