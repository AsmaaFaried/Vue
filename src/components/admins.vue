<template>
    <div>
        <h2>Admins</h2>
        <table>
            <tr>
                <th>Name</th>
                <th>age</th>
                <th>Address</th>
            </tr>
            <tr v-for="adminList,index in admins" :key="index"> 
                <td v-for="admin,index in adminList" :key="index">{{admin.username}}</td>
                <td v-for="admin,index in adminList" :key="index">{{admin.age}}</td>
                <td v-for="admin,index in adminList" :key="index">{{admin.address}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default {
        name:"adminsApp",
        inject:['admins'],
       
    }
</script>

<style scoped>

</style>