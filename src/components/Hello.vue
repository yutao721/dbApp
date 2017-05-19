<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links 李四</h2>
  </div>
</template>

<script>
  import axios from 'axios';
  export default {
    name: 'hello',
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        movieLists: []
      }
    },
    created () {
      axios.get('api/movie/in_theaters',
        {'city': '广州'})
        .then((result) => {
//          console.log(result);
          if (result.status === 200 && result.statusText === 'OK') {
            this.movieLists = result.data.subjects;
            console.log(this.movieLists)
          }
        })
        .catch((err) => {
          console.log(err);
        });
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
