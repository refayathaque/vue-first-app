<template>
  <form @submit.prevent="submitData">
    <div>
      <label>Name</label>
      <input type="text" v-model="enteredName" />
    </div>
    <div>
      <label>Phone Number</label>
      <input type="tel" v-model="enteredPhoneNumber" />
    </div>
    <div>
      <label>Email Address</label>
      <input type="email" v-model="enteredEmailAddress" />
    </div>
    <div>
      <button>Add contact</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: [ 'add-contact' ],
  data() {
    return {
      enteredName: '',
      enteredPhoneNumber: '',
      enteredEmailAddress: ''
    }
  },
  methods: {
    submitData() {
      this.$emit('add-contact', this.enteredName, this.enteredPhoneNumber, this.enteredEmailAddress)
    }
  }
}
</script>