<template>
<input class="screen" :value="showNumber"/>
</template>
<script >
export default{
    name:'Screen',
    props:{
        showNumber:String
    },
    data() {
        return {
            // showNumber:0
        }
    },
    methods: {
       
    },
}
</script>  
<style>
.screen{
  backdrop-filter: blur(5.5px);
  -webkit-backdrop-filter: blur(5.5px);
  background: rgba(255, 255, 255, 0.75);
  border: 1px solid rgba(255, 255, 255, 0.01);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(35, 35, 35, 0.1);
  color: black;
  font-size: 35px;
  overflow: auto;
  padding: 20px;
  text-align: right;
  width: 326px; 
}
</style>