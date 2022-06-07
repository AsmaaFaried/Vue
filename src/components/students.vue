<template>
    <div>
        <h2>Students</h2>
        <table >
            <tr>
                <th>Name</th>
                <th>age</th>
                <th>Address</th>
            </tr>
            <tr v-for="studentList,index in students" :key="index"> 
                <td v-for="std,index in studentList" :key="index">{{std.username}}</td>
                <td v-for="std,index in studentList" :key="index">{{std.age}}</td>
                <td v-for="std,index in studentList" :key="index">{{std.address}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
import { inject } from 'vue'

    export default {
        name:"studentsApp",
        setup(){
            const students=inject("students")
            return{
                students
            }
        }
        
    }
</script>

<style scoped>


</style>