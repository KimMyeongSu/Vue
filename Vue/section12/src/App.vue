<template>
  <form v-on:submit.prevent="submitFrom">
    <div>
      <label for="usename">id: </label>
      <input id= "usename" type="text" v-model="username">
    </div>
    <div>
      <label for="password">pw: </label>
      <input id= "password" type="password" v-model="userpassword">
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>
import axios from 'axios'
export default {
  data: function(){
    return {
      username: '',
      userpassword: ''
    }
  },
  methods: {
    submitFrom: function(){
      // event.preventDefault(); //form 의 이동 새로고침을 막음 (일반적인 자바스크립트 처리방법)
      console.log(this.username,this.userpassword);
      let url = 'https://jsonplaceholder.typicode.com/todos/users';
      let userData = {
        username: this.username,
        userpassword: this.userpassword
      }
      axios.post(url,userData)
      .then(function(response){
        console.log(response);
      })
      .catch(function(error){
        console.log(error);
      })
    }
  }

}
</script>

<style>


</style>
