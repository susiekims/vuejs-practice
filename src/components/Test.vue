<template>
  <div class="test">
    <input type="text" v-model="title" />
    <h1 v-if="showName">{{title}}</h1>
    <p v-else="showName">Nobody</p>
    <p v-text="user.firstName"></p>
    <ul>
      <li v-for="cheese in cheeses">{{cheese}}</li>
    </ul>
    <button v-on:click="greet()">Hi there</button>
    <input v-on:keyup="pressKey" />
    <hr />
    <label>First name:</label>
    <input type="text" name="name" value="" v-model="user.firstName" />
    <input type="text" name="name" value="" v-model="user.lastName" />
    <h3>{{fullName}}</h3>
    <h2>{{msg}}</h2>
  </div>
</template>

<script>
  export default {
    name: 'test',
    props: {
      msg: {
        type: String,
        default: 'Foobar',
      }
    },
    data() {
      return {
        title: 'Hello',
        user: {
          firstName: 'Susie',
          lastName: 'Kim',
        },
        showName: true,
        cheeses: ['Camembert', 'Cheddar', 'Provolone'],
        greet: function () {
          alert('hello')
        },
        pressKey: function (e) {
          console.log(e.target.value)
        }
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

</style>
