<template>
  <div id="app">
    <div class="content">
      <div class="todo">
        <form action="/todo">
          <input type="text" class="input" placeholder="ここにやることを入力しよう！" v-model="input">
          <input type="button" @click="addData" value="追加！">
        </form>
        <table>
          <tr v-for="(row, index) in data" :key="index">
            <td>{{row.todo}}</td>
            <input v-if="data.length > 0" type="button" @click="delData(row.id)" value="削除！">
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
  async fetch() {
    await this.$axios.$get('http://127.0.0.1:8000/api/todo')
    .then(response => {
        this.data = response.data;
      })
      .catch(error => {
        console.log(error);
      });
  },
  methods: {
    addData: function() {
      //下のロジックをアロー関数で書き直したい
      // this.$axios.$post('http://127.0.0.1:8000/api/todo', {todo:this.input})
      // .then(function (response) {
      //   console.log('登録処理です。');
      //   console.log(response);
      //   console.log(response.data);
      //   this.data = response.data;
      //   // this.data.splice(0,this.data.length,response.data);
      // })
      // .catch(function (error) {
      //   console.log(error);
      // });

      this.$axios.$post('http://127.0.0.1:8000/api/todo', {todo:this.input})
      .then(response => {
        this.data = response.data;
      })
      .catch(error => {
        console.log(error);
      });

      this.input = '';
    },
    delData: function(id) {
      this.$axios.$delete('http://127.0.0.1:8000/api/todo/' + id)
      .then(response => {
        this.data = response.data;
      })
      .catch(error => {
        console.log(error);
      });
    },
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
