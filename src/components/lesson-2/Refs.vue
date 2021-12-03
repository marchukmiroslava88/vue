<template>
  <div>
    <form v-if="!result">
      <div class="form-group">
        <label>Email</label>
        <input type="text" class="form-control" v-model.lazy="user.email" ref="someRef">
      </div>
      <div class="form-group">
        <label>Phone</label>
        <input type="text" class="form-control" v-model.lazy="user.phone">
      </div>
      <div class="form-group">
        <label>First Name</label>
        <input type="text" class="form-control" v-model.lazy="user.firstName">
      </div>
      <div class="form-group">
        <label>Last Name</label>
        <input type="text" class="form-control" v-model.lazy="user.lastName">
      </div>
      <div class="form-group">
        <label>Guests</label>
        <input type="button" class="btn btn-primary" value="+" @click="addGuest">
      </div>
      <div class="form-group" v-for="(guest, i) in guests" :key="guest.id">
        <input type="text" class="form-control" v-model.lazy="guest.value" ref="guestRef">
        <input type="button" class="btn btn-danger" value="-" @click="removeGuest(i)">
      </div>
      <hr>
      <button class="btn btn-success" @click.prevent="send" :disabled="!formReady">Send Data</button>
    </form>
    <div v-else>
      <h2>All done!</h2>
      <table class="table table-bordered">
        <tr>
          <td>Email</td>
          <td>{{ user.email }}</td>
        </tr>
        <tr>
          <td>Phone</td>
          <td>{{ user.phone }}</td>
        </tr>
        <tr>
          <td>FullName</td>
          <td>{{ fullName }}</td>
        </tr>
        <tr>
          <td>Guests</td>
          <table>
            <tr v-for="guest in guests" :key="guest.id">
              <td>{{ guest.value }}</td>
            </tr>
          </table>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>

export default {
  data: () => ({
    user: {
      email: '',
      phone: '',
      firstName: '',
      lastName: '',
    },
    result: false,
    guests: []
  }),
  computed: {
    fullName(){
      return `${this.user.firstName} ${this.user.lastName}`;
    },
    formReady(){
      return Object.values(this.user).every(val => val !== '');
    }
  },
  methods: {
    send(){
      this.guests = this.guests.filter(guest => guest.value);
      this.result = true;
    },
    addGuest(){
      this.guests.push({ id: this.guests.length + 1, value: '' });
      this.$nextTick(()=>{
        this.$refs.guestRef[this.guests.length - 1].focus()
      });
    },
    removeGuest(i){
      this.guests.splice(i, 1);
    },
  },
  mounted() {
    this.$refs.someRef.focus();
  }
}
</script>
