<template>
  <div class="hello container mt-5">
    <div class="row">
      <div class="col-8">
        <table class="table table-striped">
          <thead>
            <tr>
              <th scope="col">#</th>
              <th scope="col">title</th>
              <th scope="col">create time</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item, i) in listData">
              <th scope="row">{{i + 1}}</th>
              <td>{{ item.title }}</td>
              <td>{{ item.created_at }}</td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="col-4">
        右側
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      listData: []
    }
  },
  methods: {
    getData(){
      let vm = this
      vm.axios.get('http://lara-admin.amylab.tech/api/article')
        .then(function (response) {
          console.log(response);
          vm.listData = response.data.data
        })
        .catch(function (error) { // 请求失败处理
          console.log(error);
        });
    }
  },
  mounted () {
    this.getData()
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
