<template>
<div class="card-container">
<div class="card">
    <i class="fas fa-eye"></i>
    <h3>{{card.name}}</h3>
    <p v-show="!card.isReversed">Position Upright:<br> {{card.meaning_up}}</p>
    <p v-show="card.isReversed">Position Reversed: <br> {{card.meaning_rev}}</p>
</div>
</div>
    
</template>
<script>
export default {
    name :"Card",
    props: {
        card: Object,
    }
    
}
</script>
<style scoped>
.card{
    animation: slideInUp;
    animation-duration: 2s;
    border-style:solid;
    border-radius:30px;
    width: 250px;
    height: 400px;
    background-color:darkslateblue;
    border-color: darkslateblue;
}

@media only screen and (max-width: 885px) {
  /* For mobile phones: */
  [class*="card"] {
      margin: auto;
  }
  
}

.card h3{
    padding: 5%;
    color:darkslateblue;
}

.card p{
    padding: 5%;
    font-size: 11px;
    color:darkslateblue;
}

.card:hover{
    background-color: white;

}

.card-container{
    border:20px;
}

.card-container:hover{
    cursor:grab;
    animation:flip;
    animation-duration: 2s;
}

.fa-eye{
    color:white;
    font-size: 3em;
    padding-top: 8px;
}




</style>