<template>
  <div>
    <h2>Hello, {{ name }}</h2>
    <input type="text" v-model="name">
    <hr>
  </div>
</template>

<script>
export default {
  data: () => ({
    name: 'simple'
  })
}
</script>
