<template>
    <div>
        <h2>Insert New Candy</h2>
        <!--using inputs with refs to get data from form and a button that sets off function-->
        <input type="text" placeholder="name" ref="name">
        <input type="text" placeholder="image_url" ref="image_url">
        <input type="text" placeholder="description" ref="description">
        <button @click="new_candy">Create Candy</button>
    </div>
</template>

<script>

import axios from "axios"
    export default {
        methods: {
            //new candy function that takes values from the form
            new_candy() {
                let name = this.$refs[`name`].value
                let image_url = this.$refs[`image_url`].value
                let description = this.$refs[`description`].value
                //defining empty param to build with if statements
                let param = {}
                //if statments checking value of of req data
                if(name != ""){
                    param[`name`]=name
                }
                else{
                    console.log(`please fill out name box`)
                }
                if(image_url != ""){
                    param[`image_url`]=image_url
                }
                else{
                    console.log(`please fill out image box`)
                }
                if(description != ""){
                    param[`description`]=description
                }
                else{
                    console.log(`please fill out description box`)
                }
                //axios request with with params passed to create new candy in db
                axios.request({
                url:"http://127.0.0.1:5000/api/candy",
                method:"POST",
                data:param
            }).then(response =>{
                console.log(response)
            }).catch(failure =>{
                console.log(failure)
            })
            }
        },
    }
</script>

<style scoped>

</style>