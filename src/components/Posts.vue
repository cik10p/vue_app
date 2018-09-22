<template>
  <div class="ProductList">
    <input type="text" v-model="title" > <!-- v-model is "binding" to model, meaning we can have biddirectional binding. -->
    <h1>{{title}}</h1>
    
    <div>
    <table>
    <tr v-if="showName">
    <th>First name</th><td><span v-text="user.firstName"></span></td>
    </tr>
    <tr v-else>
    <th>First name</th><td><span>Not allowed</span></td>
    </tr>
    <tr>
      <th>Last name</th><td><span v-text="user.lastName"></span></td>
    </tr>
    </table>
    <ul>
      <li v-for="i in items">{{i.title}}</li>
    </ul>

    <button v-on:click="greet">Say hi!</button>
    <button v-on:click="test('Secret')">Test!</button>
    <div>
      <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">
    </div>
    <div id="computedProperties" class="border-top">
      <h3>Computed properties</h3>
      <input type="text" v-model="user.firstName"> <input type="text" v-model="user.lastName">
      <h5>{{fullName}}</h5>
    </div>
    <div class="border-top">
      
    </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'Posts',
  data () {
    return {
      title: 'This is my Posts list',
      user: {
        firstName: 'John',
        lastName: 'Doe'
      },
      showName: false,
      items: [
        {title: 'Item One'},
        {title: 'Item Two'},
        {title: 'Item Three'}
      ]
    }
  },
  methods:{
    greet: function () {
      alert("Application says HI! :)");
    },
    test: function (t) {
      alert(t);
    },
    pressKey: function(e){
      console.log(' pressed');
      console.log(e.target.value);
    },
    enterHit: function(e){
      console.log("Enter was hit");
    }
  },
  computed:{
    fullName: function(){
      return this.user.firstName+" "+this.user.lastName;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#computedProperties{
  margin-top:15px;
}
.border-top{
  border-top:1px solid #ddd;
}
</style>
