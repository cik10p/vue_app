<template>
  <div>
      <h1>This is users!</h1>
      <form v-on:submit="addUsers">
        <input type="text" v-model="newUser.name" placeholder="name" />
      <br/>
      <input type="email" v-model="newUser.email" placeholder="Email">
      <br/>
        <button type="submit">Submit</button>
      </form>
      <ul>
        <li v-for="user in users">
          <div>
              <span><input type="checkbox" class="toggle" v-model="user.contacted"></span><span :class="{contacted: user.contacted}">{{user.name}}: {{user.email}} </span> <button v-on:click="deleteUser(user)">Delete</button>
          </div>        
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'Users2',
  data () {
    return {
      newUser: {},
      users: [
        
      ]
    }
  },
  methods:{
    addUsers: function(e) {
      // console.log("Add");
      this.users.push({
        name: this.newUser.name,
        email: this.newUser.email,
        contacted: false
      });
      e.preventDefault();
    },
    deleteUser: function(user) {
      this.users.splice(this.users.indexOf(user),1)
    }
    
  },
  created: function (params) {
      // console.log("created ran");
      this.$http.get('https://jsonplaceholder.typicode.com/users')
      .then(function(response) {
        console.log(response.data);
        this.users = response.data;
      });
  },
  computed:{
  }
}
</script>

<style scoped>
  .contacted{
    text-decoration: line-through;
  }
</style>

<!--
<template>
  <div>

  </div>
</template>

<script>
export default {
  name: 'users',
  data () {
    return {
      
    }
  },
  methods:{
  },
  computed:{
  }
}
</script>

<style scoped>

</style>
-->
