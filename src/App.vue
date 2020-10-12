<template>
  <h2>My friends</h2>
  <new-friend @add-contact="addContact"></new-friend>
  <ul>
    <li v-for="friend in friends" :key="friend.id">{{ friend.name }}</li>
  </ul>
  <friend-contact
    v-for="friend in friends"
    :key="friend.id"
    :name="friend.name"
    :phone-number="friend.phoneNumber"
    :email-address="friend.emailAddress"
    :is-favorite="friend.isFavorite"
    :is-intelligent="friend.isIntelligent"
    @toggle-intelligence="toggleIntelligenceChange"
    @delete-friend="deleteContact"
  ></friend-contact>

  <!-- toggle intelligence won't work for these -->
  <friend-contact
    name="John Lorenz"
    phone-number="2023415049"
    :is-favorite="1"
  ></friend-contact>
  <friend-contact
    name="Jorge Lorenz"
    phone-number="2023415044"
    email-address="jo.lorenz@gmail.com"
    :is-favorite="0"
  ></friend-contact>
  <friend-contact
    name="Tilda Lorenz"
    email-address="t.lorenz@gmail.com"
    :is-favorite="1"
  ></friend-contact>

  <active-user></active-user>
  <user-data @submit-user-data="submitUserData"></user-data>
</template>

<script>
export default {
  data() {
    return {
      friends: [
        {
          id: 1,
          name: "Manuel Lorenz",
          phoneNumber: "2023415040",
          emailAddress: "m.lorenz@gmail.com",
          isFavorite: 1,
          isIntelligent: true,
        },
        {
          id: 2,
          name: "Julie Lorenz",
          phoneNumber: "2023415041",
          emailAddress: "j.lorenz@gmail.com",
          isFavorite: 0,
          isIntelligent: true,
        },
        {
          id: 3,
          name: "Timothy Lorenz",
          phoneNumber: "2023415099",
          emailAddress: "timo.lorenz@gmail.com",
          isFavorite: 0,
          isIntelligent: true,
        },
      ],
      userData : {
        username: '',
        age: ''
      }
    };
  },
  methods: {
    toggleIntelligenceChange(emailAddress) {
      const identifiedFriend = this.friends.find(
        (friend) => friend.emailAddress === emailAddress
      );
      identifiedFriend.isIntelligent = !identifiedFriend.isIntelligent;
    },
    addContact(name, phoneNumber, emailAddress) {
      const newFriendContact = {
        id: new Date().toISOString(),
        name,
        phoneNumber,
        emailAddress,
        isFavorite: 0,
        isIntelligent: false,
      };
      this.friends.push(newFriendContact);
    },
    deleteContact(emailAddress) {
      this.friends = this.friends.filter(
        friend => friend.emailAddress !== emailAddress
      );
    },
    submitUserData(username, age) {
      console.log(username, age)
      this.userData.username = username
      this.userData.age = age
    }
  },
};
</script>
