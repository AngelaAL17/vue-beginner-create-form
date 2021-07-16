<template>
<!--
v-on:submit.prevent: 폼의 기본적인 동작을 막기 위한 modifier
form의 기본 동작 이벤트 (새로고침)을 하지 않도록 제어하는 것
js: event.preventDefalut()와 같은 효과를 가짐
-->

  <form v-on:submit.prevent="infoReceive">
<!-- 아이디 구역 1-->
    <div>
    <label for="userid">id :</label>
    <input id="userid" type="text" v-model='userid'>
    </div>
<!-- 패스워드 구역 1-->
    <div>
    <label for="userpw">pw :</label>
    <input id="userpw" type="password" v-model='password'>
    </div>

    <button type="submit">login</button>

  </form>
</template>

<script>
// npm install --save axios 필요
import axios from 'axios';

export default {
  data:function(){
    return{
     // 여기랑 v-model이랑 연결되는 곳
     userid:"",
     password:""
    }
  },
  methods:{
    //function 만들기
    //1. data 값을 콘솔창에 찍기
    /*infoReceive:function(){
      console.log(this.userid,this.password);
    }*/
    //2. data 값을 서버로 넘기기
   infoReceive:function()
   {
     var url='https://jsonplaceholder.typicode.com/users';
     var data={
       userid:this.userid,
       password:this.password
     }

     //Post 새로운 객체 생성용 
     axios.post(url,data) // axios.post("url 주소",{data 객체})
      .then(function(response){ // then은 성공, catch는 실패
        console.log(response);
      })
      .catch(function(error){
        console.log(error);
      });
   }
    
  }
  

}
</script>

<style>

</style>