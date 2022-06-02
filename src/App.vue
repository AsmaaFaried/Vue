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
        <h3>Nothing to select</h3>
      </div>
     
      </center>
  </div>
  
</template>

<script>
import formApp from './components/form.vue'
import studentsApp from './components/students.vue'
import adminsApp from './components/admins.vue'
export default {
  components:{
    formApp,
    studentsApp,
    adminsApp
  },
  provide(){
    return {
      students:this.students,
      admins:this.admins
      }
  },
  name: 'App',
  data(){
    return{
      key:0,
      students:[],
      admins:[]
      }
    
  },
      methods:{
        formComp(){
          this.key=1;
        },
        stdsComp(){
          this.key=2;
        },
        adminsComp(){
          this.key=3;
        },
        addData(user){
          if(user.userType==='Student'){
             this.students.push({user})
          }
          if(user.userType==='Admin'){
             this.admins.push({user})
          }
        },
        
    }
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
