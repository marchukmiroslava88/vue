<template>
  <div>
    <h2>Hello, {{ name }}</h2>
    <input type="text" :value="name" @input="onInput">
    <hr>
  </div>
</template>

<script>
export default {
  data: () => ({
    name: '',
  }),
  methods: {
    onInput(e){
      this.name = e.target.value;
    }
  }
}
</script>
