<template>
  <h3>{{ name }} {{ isFavorite === 1 ? '(Favorite)' : '' }}</h3>
  <h4>{{ isIntelligent ? 'Intelligent' : '' }}</h4>
  <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
  <button @click="toggleIntelligence">Make {{ isIntelligent ? 'un' : '' }}intelligent</button>
  <ul v-if="detailsAreVisible">
    <li>Phone: {{ phoneNumber }}</li>
    <li>Email: {{ emailAddress }}</li>
  </ul>
  <button @click="$emit('delete-friend', emailAddress)">Delete</button>
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
        // 0 is false, 1 is true
      }
    },
    isIntelligent: {
      type: Boolean,
      required: false,
      default: false
    }
  },
  // emits: [ 'toggle-favorite' ],
  emits: { 
    'toggle-intelligence': (emailAddress) => {
      if (emailAddress) {
        return true
      } else {
        console.warn ('emailAddress is missing!')
        return false
      }
    },
    'delete-friend': {}   
  },
  data() {
    return {
      detailsAreVisible: false,
      // friend: {
      //   id: 'Manuel',
      //   name: 'Manuel Lorenz',
      //   phoneNumber: '2023415040',
      //   emailAddress: 'm.lorenz@gmail.com'
      // }
    }
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible
    },
    toggleIntelligence() {
      this.$emit('toggle-intelligence', this.emailAddress);
    },
    // deleteFriend() {
    //   this.$emit('delete-friend');
    // }
  }
}
</script>