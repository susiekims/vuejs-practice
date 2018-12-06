<template>
  <div class="app">
    <h1>Users</h1>
    <form v-on:submit="addUser">
      <input type="text" name="user" v-model="newUser.name" placeholder="Name" />
      <input type="text" name="user" v-model="newUser.email" placeholder="Email" />
      <input type="submit"/>
    </form>
    <ul>
      <li v-for="user in users">
        <input type="checkbox" value="" class="toggle" v-model="user.contacted" />
        <span :class="{contacted: user.contacted}">
          {{user.name}}: {{user.email}}
        </span>
        <button v-on:click="deleteUser(user)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'users',
    props: {
      
    },
    data() {
      return {
        newUser: {},
        users: [
          {
            name: 'Jon Doe',
            email: 'jondoe@gmail.com',
            contacted: false
          },
          {
            name: 'Steve Smith',
            email: 'ssmith@gmail.com',
            contacted: false
          },
          {
            name: 'Tom White',
            email: 'tom.white@gmail.com',
            contacted: false
          }

        ]
      }
    },
    methods: {
      addUser: function (e) {
        e.preventDefault();
        this.users.push({
          name: this.newUser.name,
          email: this.newUser.email,
          contacted: false
        })
      },

      deleteUser: function (user) {
        this.users.splice(this.users.indexOf(user), 1);
      }
    },
    computed: {
      fullName: function () {
        return this.user.firstName + ' ' + this.user.lastName;
      }
    }
  }
</script>
<style scoped>
  .contacted {
    text-decoration: line-through;
  }
</style>
