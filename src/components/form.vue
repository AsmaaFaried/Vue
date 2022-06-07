<template>
    <div>
        <form @submit.prevent="senduser">
            <input type="text" placeholder="Enter Name" v-model.trim="username" ref="inpref" /><br/>
            <input type="number" placeholder="Enter Age" min="0" max="100" v-model.number="age"/><br/>
            <input type="text" placeholder="Enter Address" v-model.trim="address"/><br/>
            <label><input type="radio" name="type" value="Student" v-model="userType"/>Student</label><br/>
            <label><input type="radio" name="type" value="Admin" v-model="userType"/>Admin</label><br/>
            <button>Add User</button>
        </form>
    </div>
</template>

<script>
import { reactive, ref, toRefs } from '@vue/reactivity'
import { onMounted } from 'vue'
    export default {
        name:"formApp",
        emits:['data'],
        setup(props,context){
            const inpref=ref(null)
            const userData=reactive({
                username:'',
                age:0,
                address:'',
                userType:''
            })
            onMounted(()=>{
                inpref.value.focus()
            })
            function senduser(){
                context.emit('data',userData)
            }
            return{
                ...toRefs(userData),senduser,inpref
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