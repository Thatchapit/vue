<template>
<div class="hello">
  <h1>{{ msg }}</h1>

  <input placeholder="Search by name" v-model="name" />
    <h2>{{name}}</h2>
  <div class="container">
    <div class="row">
      <div class="col-xs-12">
        <table class="table">
          <caption>= Table Name =</caption>
          <thead>
            <tr>
              <th>#No.</th>
              <th>Image</th>
              <th>Eng Name</th>
              <th>Date Time</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in filteredItems" style="text-align:left">
              <th>{{item.id}}</th>
              <td><img class="img-responsive" :src="imagePath(item.id)"></td>
              <td>{{item.ename}}</td>
              <td>{{item.base.HP}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <!-- <button type="button" class="btn btn-primary" name="button" v-on:click="pressed">Add NOW</button> -->
  </div>
</div>
</template>

<script>

import  apiURL from '../assets/pokedex.json'
export default {
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      name: '',
      items: apiURL,

    }
  },
  created: function(){

  },
  computed: {
    filteredItems() {
      var that = this;


      return that.items.filter(value => {

         return value.ename.toLowerCase().indexOf(that.name.toLowerCase()) >= 0 
      })
    }
  },
  methods: {
    imagePath: function (path) {
      return require('../assets/spr/'+path+'MS.png')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
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
