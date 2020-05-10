<template>
  <div class="hello container">
    <div class="media" v-for="item in messages">
      <img v-if="item.username != username" src="https://fakeimg.pl/60/" class="align-self-start mr-3" alt="...">
      <div class="media-body">
        <h5 class="mt-0">{{ item.username }}</h5>
        <p>{{ item.message }}</p>
      </div>
      <img v-if="item.username == username" src="https://fakeimg.pl/60/" class="align-self-start mr-3" alt="...">
    </div>
    <div class="input-group mb-3">
      <input type="text" class="form-control" v-model="message" placeholder="輸入訊息" aria-label="輸入訊息" aria-describedby="button-addon2">
      <div class="input-group-append">
        <button class="btn btn-outline-primary" @click="submitMessage" type="button" id="button-addon2">送出</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld2',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      username: 'Amy',
      message: '',
      messages: [
        {
          username: 'Amy',
          message: 'Hello 你好'
        },
        {
          username: 'John',
          message: '你也好'
        }
      ]
    }
  },
  methods: {
    submitMessage () {
      let vm = this
      vm.messages.push({
        username: vm.username,
        message: vm.message
      })
      vm.message=''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
