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
function getSale(promo){
  switch (promo){
    case 'some':
      return 10;
    case 'other':
      return 20;
    default:
      return 0;
  }
}
export default {
  data: () => ({
    promo: '',
    price: 1000,
  }),
  computed: {
    sale(){
      return getSale(this.promo);
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
