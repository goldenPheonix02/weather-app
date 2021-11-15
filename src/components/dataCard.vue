<template lang="">
    <div class="container">
        <Input @submitted="OnSubmit" />
        <div class="date">
            <p class="day">{{ date }}</p>
            <p class="time">{{ time }} </p>
        </div>
        <div class="temp">
            <p>{{temp}} <sup>o</sup> C</p>
        </div>
        <div class="clouds">
            <p>{{ clouds }}</p>
            <!-- <p>{{city}}</p> -->
        </div>
        
    </div>
</template>
<script>
import Input from "@/components/input.vue";
export default {
    name:'DataCard',
    components:{
        Input,
    },
    data(){
        return{
            date:'Thursday, 6 Jan',
            time:'23:45 PM',
            temp:27,
            city:'London',
            clouds:'Clouds'
        };
    },
    methods:{
        OnSubmit(name){
            console.log(name);
        }

    },

    
}
</script>
<style scoped>
.container{
    text-align: center;
    display: inline-block;
    padding:1rem 5rem 10rem;
    border-radius:5px;
    margin:30px auto;
}
.date{margin:20px 0 0;}
.day{font-size: 2rem;}
.time,.clouds{font-size: 1.2rem;word-spacing:3px;}
p:nth-child(1){
    line-height: 2;
}
.temp{
    position: relative;
    margin:0px auto;
    font-size:4.2rem;
    /* border:1px solid #333; */
    padding:0rem 0;
}


</style>