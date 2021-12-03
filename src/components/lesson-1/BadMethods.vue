<template>
  <div>
    <input type="text" v-model.trim="firstName">
    <input type="text" v-model.trim="lastName">
    <div>
      {{ fullName() }}
    </div>
    <button type="button" class="btn btn-info" @click="isShow = !isShow">Toggle</button>
    <div v-if="isShow">some text</div>
    <hr>
  </div>
</template>

<script>
export default {
  data: () => ({
    firstName: '',
    lastName: '',
    isShow: false,
  }),
  methods: {
    fullName(){
      console.log('поля не кешируются')
      return `${this.firstName} ${this.lastName}`;
    },
  }
}
</script>
