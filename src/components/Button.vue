<template>
<button class="btn" @click="onClick()"><i class="fas fa-bolt"></i> {{text}}</button>
    
</template>
<script>


export default {
    name:'Button',
    props:{
        text: String,

    },
    components:{

    },
    methods:{
    onClick(){
        this.$emit('btn-click');
    }

    }
    
}
</script>
<style scoped>

.btn{
  width: 60%;
  height: 50px;
  border-radius: 30px;
  border-style:none;
  font-family: 'Noto Serif SC', serif;
  margin: 1%;
}

.btn:hover{
    background-color:black;
    color:blanchedalmond;
    cursor:pointer
}

.btn:active{
    background-color: darkslateblue;
    color:blanchedalmond;
    cursor:wait;
}
</style>