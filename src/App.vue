<template>
<div>
  <table border="" align="center" width="50%">
    <tr>
      <td>id</td>
      <td>nama</td>
      <td>aksi</td>
    </tr>
    <tr v-for="user of users" :key="users.id">
      <td>
        <span>{{ user.id+1 }}</span>
      </td>
      <td>
        <span>{{ user.name }}</span>
      </td>
      <td>
      <button @click="edit(user)">Edit</button> ||  <button @click="del(user)">Delete</button>
      </td>
    </tr>
      <button class="w-full">add</button>
  </table>
</div>    
</template>





<script>
/* eslint-disable */
import axios from 'axios'
export default {
  data(){
    return{
        users: []
    }
  },
  mounted() {
    this.load()
  },
  methods: {
    load(){
        axios.get('http://localhost:3000/users').then(res => {
        this.users = res.data //respon dari rest api dimasukan ke users
      }).catch ((err) => {
        console.log(err);
      })
    }
   }
  }
</script>

