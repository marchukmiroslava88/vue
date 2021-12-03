<template>
  <div>
    <h2>Hello, {{ name }}</h2>
    <input type="text" v-bind:value="name" v-on:input="name = $event.target.value">
    <hr>
  </div>
</template>

<script>
export default {
  data: () => ({
    name: ''
  })
}
</script>
