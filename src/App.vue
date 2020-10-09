<template>
  <h2>My friends</h2>
  <ul>
    <friend-contact v-for="(friend, index) in friends" :key="index" :name="friend.name" :phone-number="friend.phoneNumber" :email-address="friend.emailAddress" :is-favorite="friend.isFavorite"></friend-contact>
    <friend-contact name="John Lorenz" phone-number="2023415049" :is-favorite="1"></friend-contact>
    <friend-contact name="Jorge Lorenz" phone-number="2023415044" email-address="jo.lorenz@gmail.com" :is-favorite="0"></friend-contact>
    <friend-contact name="Tilda Lorenz" email-address="t.lorenz@gmail.com" :is-favorite="1"></friend-contact>
    <li v-for="(friend, index) in friends" :key="index">{{ friend.name }}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      friends: [
        {
          id: 'Manuel',
          name: 'Manuel Lorenz',
          phoneNumber: '2023415040',
          emailAddress: 'm.lorenz@gmail.com',
          isFavorite: 1
        },
        {
          id: 'Julie',
          name: 'Julie Lorenz',
          phoneNumber: '2023415041 ',
          emailAddress: 'j.lorenz@gmail.com',
          isFavorite: 0
        }
      ]
    }
  }
}
</script>