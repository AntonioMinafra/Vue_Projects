<template>
  <section>
        <header>
            <h1>My Friends</h1>
        </header>
        <ul>
          <friend-contact v-for="friend in friends"
          :key="friend.id"
          :id="friend.id"
          :name="friend.name"
          :phone-number="friend.phone"
          :email-address="friend.email"
          :is-favorite="friend.isFavorite"
          @toggle-favorite="toggleFavoriteStatus"
          ></friend-contact>
        </ul>
    </section>
</template>

<script>

export default {
  data() {
    return {
      friends: [
      {
        id: "Manuel",
        name: "Manuel Lorenz",
        phone: "2345 234 56",
        email: "manuel@gmail.com",
        isFavorite: true,
      },
      {
        id: "tony",
        name: "Tony Lorenz",
        phone: "2335 294 46",
        email: "tony@gmail.com",
        isFavorite: false,

      },
      ]
    }
  },
  methods: {
    toggleFavoriteStatus(friendId) {
      const identifiedFriend = this.friends.find( friend => friend.id === friendId);
      identifiedFriend.isFavorite = !identifiedFriend.isFavorite;
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Jost&display=swap');
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
