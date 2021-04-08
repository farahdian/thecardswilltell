<template>
<div class="container">
  
  <Header title="What's in the cards for you?" class="header animate__animated animate__slideInDown"/>
  
  <div class="spread">

  <div v-bind:key="card.id" v-for="card in cards">
    <h2>{{card.time == "PAST" ? "PAST" : (card.time == "PRESENT" ? "PRESENT" : "FUTURE")}}</h2>
     <Card :card="card"/> 
  </div> 

  </div>

  <div class="footer">
  <Button @btn-click="fetchNewCards" text="Deal a new fortune"/>
  </div>
</div>
  
</template>

<script>
import Header from './components/Header';
import Button from './components/Button';
import Card from './components/Card';


export default {
  name: 'App',
  components: {
    Header,
    Button,
    Card,
   
  },
  data(){
    return{
      cards:[],
      arr: ["UPRIGHT", "REVERSED"],
    }
  },
  methods: {
    async fetchCards(){
      const res = await fetch('https://rws-cards-api.herokuapp.com/api/v1/cards/random?n=3')
      const data = await res.json()
      .then(
        results =>{
          const cardRes = results.cards
          const newCards =[]

          for(let i = 0; i < cardRes.length; i++){
            const random = this.arr[Math.floor(Math.random()*this.arr.length)];
            const card = cardRes[i];
            const newCard = {...card, isReversed: random =="REVERSED"? true:false, time : i == 0 ? "PAST" : (i == 1 ? "PRESENT" : "FUTURE"),}
            /**
             * random == "REVERSED" ?true:false
             * 
             * is the same as 
             * 
             * if (random =="REVERESED"){
             * return true
             * }else {
             * return false
             * }
             * 
             * if (i == 0){
             * return "PAST"
             * } else {
             *  if (i == 1){
             * return "PRESENT"
             * } else 
             * {
             * return "FUTURE"
             * }
             * 
             * 
             * 
             * 
             */
            

            newCards.push(newCard);
            
            
              }    
          return newCards; 
              
        } 
      )
      console.log(data)
      return data     
    },
    async fetchNewCards(){
      this.cards =await this.fetchCards()
      alert('Your fortune is at your fingertips')
    }
  },
  async created(){
    this.cards = await this.fetchCards()
    

  }
}




</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Serif+SC:wght@200;300;400;500;600;700;900&display=swap');

body{
  margin: 0;
  padding: 0;
  font-family: 'Noto Serif SC', serif;
  text-align: center;
  background: linear-gradient(
        to right, rgba(106,90,205,0.75),
        rgba(255,99,71,0.75));
}

.container{
  display: inline;
  justify-content: center;
  margin: 5%;
  padding: 5%;

}




.spread{
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  margin: 1%;
  padding: 1%;
}

@media only screen and (max-width: 885px) {
  /* For mobile phones: */
  [class*="spread"] {
    padding: auto;
    display: flex;
    flex-direction: column;
    justify-items: center;
    justify-content: space-around;
  }

}


.footer{
  justify-content: space-around;
}



</style>
