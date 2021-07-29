<template>
  <Layout>
    <div class="product-listing-wrapper">
      <h1 class="title">Our Food</h1>
      <p
        class="paragraph products-layout" 
      >เมนูอาหารสุดพิเศษของพวกเรา สำหรับคนกลางคืนเช่นคุณ โปรดเลือกเมนูเพื่อดำเนินการต่อ!!</p>
      <ul>
      <li v-for="foods in $page.FoodPandee.foods" :key="foods.id" class="food_li">
        <div @click="goTo(foods.id)" class="food_containers">
          <img :src= foods.image[0].url class="food_img">
          <p class="food_info">{{foods.name}} {{ foods.price }}</p>
        </div>
      </li>
    </ul>
    </div>
  </Layout>
</template>
<style lang="scss"scoped>
@import "~/theme/_main.scss";

.food_li{
  list-style:none;
  display:block;
  margin-bottom: 30px;

 
}
.food_containers{
  width: inherit;
  display: flex;
  float:left;
}
.food_info{
  color:white;
   font-family: "Jost", sans-serif;
    font-weight: 600;
    margin-left: 40px;
    text-align: center;
    align-items: center;
    margin-top: 20%;
}
.food_img{
  width: 100%;
  max-width:350px;
  margin-bottom: 50px;
  cursor: pointer;

}
.test{
  color:white;
}
.cards-wrapper {
  width: 67%;
}

.products-layout.paragraph {
  margin: 29px auto 42px;
  width: 60%;
}

.product-listing-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  color:white;
}

@media only screen and (max-width: 768px) {
  .cards-wrapper {
    width: 50%;
  }
  .products-layout.paragraph {
    width: 80%;
  }
}
</style>
<script>
import Cards from "~/components/Cards.vue";

export default {
  components: {
    Cards
  },
  metaInfo: {
    title: "Products"
  },methods: {
    goTo: function(string){
      this.$router.push('/foods/'+string); 
    }
  },
   data() {
    return {
      foods:[{
        id:'',
        name:'',
        price:'',
        image:{
          url:''
        }
      }]
    }
  },created(){
    this.foods = this.$page.FoodPandee.foods
  }
};
</script>
<page-query>
  {
    FoodPandee {
      foods {
        id
        name
        price
        image{
          url
        }
      }
    }
  }
</page-query>