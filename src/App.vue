<template>
  <div>
    <center>
      <button  @click="formComp">Form</button>
      <button  @click="stdsComp">Students</button>
      <button  @click="adminsComp">Admins</button>
    </center>
    <center >
      
      <div v-if="key==1">
        <form-app @data="addData"/>
      </div>
      <div v-else-if="key==2">
        <students-app/>
      </div>
      <div v-else-if="key==3">
        <admins-app/>
      </div>
      <div v-else>
        <form-app @data="addData"/>
      </div>
     
      </center>
  </div>
  
</template>

<script>
import formApp from './components/form.vue'
import studentsApp from './components/students.vue'
import adminsApp from './components/admins.vue'
import { provide, ref } from 'vue'
export default {
  components:{
    formApp,
    studentsApp,
    adminsApp
  },
  name: 'App',
  setup(){
    const key=ref(0)
    const students=ref([])
    const admins=ref([])

    provide('students',students)
    provide('admins',admins)

    function formComp(){
        this.key=1;
        }
    function stdsComp(){
          this.key=2;
        }
    function adminsComp(){
          this.key=3;
        }
    function addData(user){
          if(user.userType==='Student'){
            students.value.push({user})
          }
          if(user.userType==='Admin'){
            admins.value.push({user})
          }
        }
    return{
      key,
      students,
      admins,
      formComp,
      stdsComp,
      adminsComp,
      addData
    }
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
    margin: 18px;
    width: 122px;
    height: 37px;
    background-color: black;
    color: aliceblue;
    border-radius: 5px;
    font-weight: bold;
}
table {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 30%;
}

table td, table th {
  border: 1px solid #ddd;
  padding: 8px;
}

table tr:nth-child(even){background-color: #f2f2f2;}

table tr:hover {background-color: #ddd;}

table th {
  padding-top: 12px;
  padding-bottom: 12px;
  background-color: black;
  color: white;
}
</style>
