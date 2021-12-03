<template>
  <div class="wrapper">
    <div class="sample">
      <form>
        <div class="content alert alert-info" @scroll="foo">
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
          <p>This text no one reads. This text no one reads. This text no one reads.</p>
        </div>
        <div :class="{'d-none': !scrolled}">
          <div class="form-check">
            <label class="form-check-label">
              <input class="form-check-input" type="checkbox" v-model="agree">
              agree
            </label>
          </div>
          <div class="form-check">
            <label class="form-check-label">
              <div>
                <label>phone</label>
                <input class="form-check-input" type="radio" value="phone" v-model="someVal">
              </div>
              <div>
                <label>email</label>
                <input class="form-check-input" type="radio" value="email" v-model="someVal">
              </div>
            </label>
          </div>
          <hr>
          <button class="btn btn-primary" :disabled="!agree">
            Send Data
          </button>
        </div>
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
    agree: false,
    someVal: 'phone',
    scrolled: false
  }),
  methods: {
    foo(e){
      const element = e.target;
      if (element.scrollHeight - element.scrollTop === element.clientHeight)
      {
       this.scrolled = true;
      }
    }
  }
}
</script>
