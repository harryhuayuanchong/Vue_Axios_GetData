<template>
  <div>
    <h1>Vue JS + Axios => Get Data</h1>
    <div>
      <div class="post" v-for="post in posts" :key="post.id">
        <h3>Title: {{ post.title }}</h3>
        <p>Description: {{ post.body }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'AxiosPractice',
  data() {
    return {
      posts: []
    }
  },
  mounted() {
    var self = this;
    axios.get('https://jsonplaceholder.typicode.com/posts')
    .then((res) => {
      self.posts = res.data;
      console.log('Data: ', res);
    })
    .catch((err) => {
      console.log('Error: ', err)
    })
  }
}
</script>

<style type="text/css">
.post {
  background: #ccc;
  margin-bottom: 20px;
  padding: 10px 20px;
}
h3 {
  text-align: left;
}
p {
  text-align: left;
}
</style>
