<template>
  <div>
    <ul>
      <li v-for="number in numbers" :key="number">{{number}}</li>
    </ul>
  </div>
</template>

<script>

export default {
  data: () => ({
    numbers: [1,2,3],
  }),
}
</script>
