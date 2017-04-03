<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{detail}}</h2>
    <input v-model="detail"/>
    <ul>
      <li v-for="item in items">
        {{item.test}}
      </li>
    </ul>
    <button type="button" name="button" v-on:click="pressed">Alert NOW</button>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      detail: '~ Page using Vue.js ~',
      items:[
        {test:"hello"},
        {test:"world"}
      ]
    }
  },
  methods:{
      pressed(){
        alert("Wow!");
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
