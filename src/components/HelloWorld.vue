<template>
  <div class="hello">
    <li v-for="name in animal" v-bind:key="name">
      <p><strong>{{name}}</strong></p>
    </li>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      animal: null
    }
  },
  async mounted () {
    axios
      .get('http://localhost:65299/api/values')
      .then(response => (this.animal = response.data))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
