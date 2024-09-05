<template>
  <section>
        <header>
            <h1>My Friends</h1>
        </header>
        <ul>
          <friend-contact
          name="Manuel Lorenz"
          phone-number="123 456 789"
          email-address="Manuel@gmail.com"
          is-favorite="1"
          ></friend-contact>
          <friend-contact
          name="Giulia Rossi"
          phone-number="133 4596 782"
          email-address="Giulia@gmail.com"
          is-favorite="0"
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
      },
      {
        id: "tony",
        name: "Tony Lorenz",
        phone: "2335 294 46",
        email: "tony@gmail.com",
      },
      ]
    }
  },
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
