<template>
  <div>
    <input type="text" v-model.trim="promo">
    <div v-if="salePrice">
      <div>Price: {{ price }} - sale: {{salePrice}}</div>
      <div>Total price: {{ totalPrice }}</div>
    </div>
    <div v-else>
      <div>{{ totalPrice }}</div>
    </div>
    <hr>
  </div>
</template>

<script>
function getSale(promo, onComplete){

  let sale = 0;

  switch (promo){
    case 'some':
      sale = 10;
      break;
    case 'other':
      sale = 20;
      break;
    default:
      sale = 0;
      break;
  }

  setTimeout(()=>{
    onComplete(sale);
  },500);
}
export default {
  data: () => ({
    promo: '',
    price: 1000,
  }),
  computed: {
    // eslint-disable-next-line vue/return-in-computed-property
    sale(){
      getSale(this.promo, function(sale){
        console.log(sale);
      });
    },
    totalPrice(){
      return this.price * (1 - this.sale / 100);
    },
    salePrice(){
      return this.price - this.totalPrice;
    }
  }
}
</script>
