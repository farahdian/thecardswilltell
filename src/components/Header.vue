<!--HTML-->
<template>
    <h1><i class="fas fa-cloud-moon"></i>{{title}} <i class="fas fa-bahai"></i></h1>
</template>
<!--logic-->
<script>
export default {
    name: 'Header',
    props: {
        title: String
    },
    components:{

    }
    
}

</script>
<!--css-->
<style scoped>
.header{

  position: fixed top;
  text-align: center;
  width: 100%;

}

</style>