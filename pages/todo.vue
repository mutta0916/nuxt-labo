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
            <td>{{row.memo}}</td>
            <input v-if="data.length > 0" type="button" @click="delData(index)" value="削除！">
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
  async asyncData({ $axios }) {
    const data = await $axios.$get('http://127.0.0.1:8000/api/todo')
    return { data }
  },
  methods: {
    //こういう書き方もできる。
    // fetchSomething() {
    //   this.$axios.$get('http://127.0.0.1:8000/api/test')
    //   .then(response => {
    //     this.data = JSON.stringify(response)
    //   })
    // },
    addData: function() {
      this.$axios.$post('http://127.0.0.1:8000/api/todo', {id:4, memo:this.input})
      .then(function (response) {
        console.log(response);
      })
      .catch(function (error) {
        console.log(error);
      });

      this.data = this.$axios.$get('http://127.0.0.1:8000/api/todo')
      .then(function (response) {
        console.log(response);
      })
      .catch(function (error) {
        console.log(error);
      });
  
      // this.$data = this.$axios.$get('http://127.0.0.1:8000/api/todo');
      this.input = '';
    },
    delData: function(index) {
      this.data.splice(index,1);
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
