<template lang="">
    <div>
        <form @submit="submitted">
            <input  v-model="cityName" type="text" placeholder="Enter City name..." required>
            <!-- <input  v-model="cityName" type="submit"> -->
            <button type="submit">Get Weather Data</button>
        </form>
    </div>
</template>
<script>
export default {
    name:'Input',
    data(){
        return{
            cityName:'',
        }
    },
    methods:{
        submitted(e){
            e.preventDefault()
            if(!this.cityName){
                alert("Please add a task!")
                return
            }
            else{
            this.$emit('submitted',this.cityName);
        }
        this.cityName='';
        }
    }
    
}
</script>
<style scoped>
    form{
        margin:0px 0 10px; 
    }
    input{
        width:300px;
        font-size: 1rem;
        height:30px;
        display: block;
        margin:auto;
        border-radius:10px 0 10px 0;
        border:2.5px #333 solid;
    }
    button{
        border:2.5px #333 solid;
        height:40px;
        padding:0 3%;
        background: #fff;
        margin-top:20px;
        transition: all .3s;
    }
    button:hover{
        cursor: pointer;
        color:#fff;
        background: #333;
    }
</style>