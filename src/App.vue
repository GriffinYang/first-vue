<template>
  <section>
    <header><h1>My Friends</h1></header>
    <ul>
      <new-friend @friend-add="addFriend"></new-friend>
      <friend-contact
        v-for="friend in friends"
        :id="friend.id"
        :key="friend.id"
        :name="friend.name"
        :phone-number="friend.phone"
        :email-address="friend.email"
        :is-favoriated="friend.favoriate"
        @toggle-favoriate="toggleFavoriteStatus"
        @delete-friend="removeFriend"
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
          id: 'manuel',
          name: 'Manuel Lorenz',
          phone: '17764484851',
          email: 'manuel@gmail.com',
          favoriate: false,
        },
        {
          id: 'julie',
          name: 'Julie Lorenz',
          phone: '13162912058',
          email: 'julie@gmail.com',
          favoriate: false,
        },
      ],
    };
  },
  methods: {
    toggleFavoriteStatus(friendID) {
      const indentifiedFriend = this.friends.find(
        (friend) => friend.id === friendID
      );
      indentifiedFriend.favoriate = !indentifiedFriend.favoriate;
    },
    addFriend(name, phone, email) {
      const newFriend = {};
      newFriend.id = new Date() + phone;
      newFriend.name = name;
      newFriend.email = email;
      newFriend.phone = phone;
      newFriend.favoriate = false;
      this.friends.push(newFriend);
    },
    removeFriend(id) {
      const index = this.friends.findIndex((friend) => friend.id == id);
      this.friends.splice(index, 1);
    },
  },
};
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Jost&display=swap');
* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li,
form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
#app input {
  font: inherit;
  padding: 0.15rem;
}
#app label {
  font-weight: bold;
  margin-right: 0.25rem;
  width: 7rem;
  display: inline-block;
}

#app .form-container {
  display: flex;
  justify-content: center;
}
#app .submit {
  background-color: #58004d;
  color: white;
  border-radius: 5px;
  margin-top: 5px;
}
</style>
