<template>
  <div id="app">
      <div class="content">
        <b-button class="ajax-button" variant="primary" @click="fetchSomething">データを取得する！</b-button>
      </div>
      {{data}}
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
    text-align: center;
}

.ajax-button {
    margin: 50px;
}

input {
    width: 100%;
    height: 100px;
}
</style>
