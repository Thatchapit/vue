<template>
<div class="hello">
  <h1>{{ msg }}</h1>

  <input placeholder="Firstname Lastname" v-model="detail" />
    <h2>{{detail}}</h2>
  <div class="container">
    <div class="row">
      <div class="col-xs-12">
        <table class="table">
          <caption>= Table Name =</caption>
          <thead>
            <tr>
              <th>#No.</th>
              <th>First Name</th>
              <th>Eng Name</th>
              <th>Date Time</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item,count) in items" style="text-align:left">
              <th>{{item.id}}</th>

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
import  apiURL  from '../assets/pokedex.json'

export default {
  name: 'hello',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      detail: '',
      items: []
    }
  },
  created: function(){
    this.fetchData();
  },
  methods: {
    // pressed() {
    //
    //   if (this.detail !== "") {
    //     let name = []
    //     let date = new Date().toISOString().slice(0, 10);
    //
    //     name = this.detail.split(" ");
    //     this.items.push({
    //       firstname: name[0],
    //       lastname: name[1],
    //       time: date
    //     });
    //     this.detail = "";
    //   }else{
    //     alert("Input Your Name!");
    //   }
    // },
    fetchData() {

    var self = this;
    $.get( apiURL, function( data ) {
      console.log(data);
     self.items = data;
     });
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
