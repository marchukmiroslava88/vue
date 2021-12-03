<template>
  <div>
    <button @click="addNumber">Add</button>
    <hr>
    <ul class="list-group">
      <li :key="i"
          class="list-group-item"
          v-for="(number, i) in numbers"
          @click="onDouble(i)"
      >{{ i }} | {{ number.value }}</li>
    </ul>
  </div>
</template>

<script>

export default {
  data: () => ({
    numbers: [],
  }),
  methods: {
    addNumber(){
      this.numbers.push({ value: Math.random() });
    },
    onDouble(i){
      this.numbers[i].value *= 2;
    }
  }
}
</script>
