<template>
  <div>
      <h1>This is users!</h1>
      <form v-on:submit="addUsers">
        <input type="text" v-model="newUser.firstName" placeholder="First name" /> <input type="text" v-model="newUser.lastName" placeholder="Last name">
      <br/>
      <input type="email" v-model="newUser.email" placeholder="Email">
      <br/>
        <button type="submit">Submit</button>
      </form>
      <ul>
        <li v-for="user in users">
          <div>
              <span><input type="checkbox" class="toggle" v-model="user.contacted"></span><span :class="{contacted: user.contacted}">{{user.firstName}} {{user.lastName}}: {{user.email}} </span> <button v-on:click="deleteUser(user)">Delete</button>
          </div>        
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'Users',
  data () {
    return {
      newUser: {},
      users: [
        {
          firstName: "John",
          lastName: 'Doe',
          email: 'john@doe.com',
          age: 19,
          contacted: false,
          favoriteArtists: ['Scooter', 'ACDC', 'Queen']
        },
        {
          firstName: "Mike",
          lastName: 'Tison',
          email: 'mike@tison.com',
          age: 25,
          contacted: false,
          favoriteArtists: ['G&G Sindikatas', 'Ruta Scegolovaite', 'Scorpions']
        },
        {
          firstName: "Sarah",
          lastName: 'Conor',
          email: 'sarah@conor.com',
          age: 33,
          contacted: false,
          favoriteArtists: ['The Beatles', 'Tiesto', 'Eagles']
        }
      ]
    }
  },
  methods:{
    addUsers: function(e) {
      // console.log("Add");
      this.users.push({
        firstName: this.newUser.firstName,
        lastName: this.newUser.lastName,
        email: this.newUser.email,
        contacted: false
      });
      e.preventDefault();
    },
    deleteUser: function(user) {
      this.users.splice(this.users.indexOf(user),1)
    }
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
