<template>
  <li>
    <h2>{{ name }} {{ isFavorite === 1 ? '(Favorite)' : '' }}</h2>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li>Phone: {{ phoneNumber }}</li>
      <li>Email: {{ emailAddress }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  // props: [ 'name', 'phoneNumber', 'emailAddress' ],
  props: {
    name: String,
    phoneNumber: {
      type: String,
      required: false,
      default: () => {
        return '1234567890'
      }
    },
    emailAddress: {
      type: String,
      required: false,
      default: 'helloWorld@gmail.com',
    },
    isFavorite: {
      type: Number,
      required: true,
      validator: (value) => {
        return value === 0 || value === 1
      }
    }
  },
  data() {
    return {
      detailsAreVisible: false,
      friend: {
        id: 'Manuel',
        name: 'Manuel Lorenz',
        phoneNumber: '2023415040',
        emailAddress: 'm.lorenz@gmail.com'
      }
    }
  },
  methods: {
    toggleDetails() {
      console.log(this.name, this.phoneNumber, this.emailAddress)
      this.detailsAreVisible = !this.detailsAreVisible
    }
  }
}
</script>