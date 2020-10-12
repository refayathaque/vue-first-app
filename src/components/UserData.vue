<template>
  <p>User Data Component</p>
  <form @submit.prevent="submitData">
    <div>
      <label>Username</label>
      <input type="text" v-model="enteredUsername" />
    </div>
    <div>
      <label>Age</label>
      <input type="text" v-model="enteredAge" />
    </div>
    <div>
      <button>Submit user data</button>
    </div>
  </form>
</template>

<script>
export default {
  // 'emitting custom events'
  emits: [ 'submit-user-data' ],
  data() {
    return {
      enteredUsername: '',
      enteredAge: '',
    }
  },
  methods: {
    submitData() {
      this.$emit('submit-user-data', this.enteredUsername, this.enteredAge)
    }
  }
}
</script>