<template>
    <div>
        <form @submit.prevent="addUser">
            <input type="text" placeholder="Enter Name" v-model.trim="userData.username" /><br/>
            <input type="number" placeholder="Enter Age" min="0" max="100" v-model.number="userData.age"/><br/>
            <input type="text" placeholder="Enter Address" v-model.trim="userData.address"/><br/>
            <label><input type="radio" name="type" value="Student" v-model="userData.userType"/>Student</label><br/>
            <label><input type="radio" name="type" value="Admin" v-model="userData.userType"/>Admin</label><br/>
            <button @click="$emit('data',userData)">Add User</button>
        </form>
    </div>
</template>

<script>
    export default {
        name:"formApp",
        emits:['data'],
        data(){
            return{
                userData:{
                    username:'',
                    age:0,
                    address:'',
                    userType:''
                }
            }
        },
        methods:{
            addUser(){
                console.log('User : ',this.userData)
            }
        }
    }
</script>

<style scoped>
form{
    background-color: black;
    width: 30%;
    padding: 35px;
    border-radius: 20px;

}
input[type='text'],input[type='number'],button{
    border-radius: 9px;
    width: 300px;
    height: 35px;
    margin: 5px;
    text-align: center;
}
label{
    color: aliceblue;
}
button{
    background-color: #41b8ff;
}
</style>