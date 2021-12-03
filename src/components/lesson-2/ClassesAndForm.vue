<template>
  <div class="sample">
    <div class="alert" :class="alertClasses">
      Some text
    </div>
    <div class="form-check">
      <div>
        <label class="form-check-label">
          <input class="form-check-input" type="radio" value="green" v-model="alertType">
          Green
        </label>
      </div>
      <div>
        <label class="form-check-label">
          <input class="form-check-input" type="radio" value="orange" v-model="alertType">
          Orange
        </label>
      </div>
      <div>
        <label class="form-check-label">
          <input class="form-check-input" type="radio" value="red" v-model="alertType">
          Red
        </label>
      </div>
    </div>
    <hr>
    <div class="form-check">
      <div v-for="(value, name) in tableClasess" :key="name">
        <label class="form-check-label">
          <input class="form-check-input" type="checkbox" v-model="tableClasess[name]">
          {{ name }}
        </label>
      </div>
    </div>
    <hr>
    <table class="table" :class="tableClasess">
      <tr>
        <td>Title</td>
        <td>Some</td>
        <td>nz</td>
      </tr>
      <tr>
        <td>Title</td>
        <td>Some</td>
        <td>nz</td>
      </tr>
      <tr>
        <td>Title</td>
        <td>Some</td>
        <td>nz</td>
      </tr>
    </table>
    {{ alertType }}
    {{ tableClasess }}
  </div>
</template>

<script>

export default {
  data: () => ({
    alertType: 'green',
    tableClasess: {
      'table-hover': false,
      'table-bordered': false,
      'table-some': false
    }
  }),
  computed: {
    alertClasses(){
      return {
        'alert-success': this.alertType === 'green',
        'alert-warning': this.alertType === 'orange',
        'alert-danger': this.alertType === 'red'
      }
    }
  }
}
</script>
