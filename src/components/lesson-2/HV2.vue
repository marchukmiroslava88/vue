<template>
  <div class="wrapper">
    <div class="sample">
      <form>
        <div class="progress">
          <div class="progress-bar"></div>
        </div>
        <div>
          <div class="form-group" v-for="(field, i) in info" :key="field.name">
            <label>{{ field.name }}</label>
            <span v-if="field.error"
                  class="fa"
                  :class="field.error ? 'fa-check-circle text-success' : 'fa-exclamation-circle text-danger'"></span>
            <input type="text" class="form-control" :value="field.value" @change="validate(i, $event)">
          </div>
        </div>
        <button class="btn btn-primary">
          Send Data
        </button>
      </form>
      <div>
        <table class="table table-bordered">
          <tr>
            <td></td>
            <td></td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>
<style>
.content{
  height: 300px;
  overflow: auto;
}
</style>
<script>

export default {
  data: () => ({
    info: [
      {
        name: 'Name',
        value: '',
        pattern: /^[a-zA-Z ]{2,30}$/,
        error: false
      },
      {
        name: 'Phone',
        value: '',
        pattern: /^[0-9]{7,14}$/,
        error: false
      },
      {
        name: 'Email',
        value: '',
        pattern: /.+/,
        error: false
      },
      {
        name: 'Some Field 1',
        value: '',
        pattern: /.+/,
        error: false
      },
      {
        name: 'Some Field 2',
        value: '',
        pattern: /.+/,
        error: false
      }
    ],
    errors: []
  }),
  methods: {
    validate(i, e){
      let field = this.info[i];
      field.error = field.pattern.test(e.target.value)
    }
  }
}
</script>
