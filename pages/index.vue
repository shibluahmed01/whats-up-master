<template>
  <div class="container">
    <form class="main">
      <h2>Login</h2>
      <input
        class="email"
        type="email"
        placeholder="Email address..."
        v-model="email"
      />
      <br />
      <input
        class="password"
        type="password"
        placeholder="password..."
        v-model="password"
      />
      <br />
      <button type="submit" @click.prevent="register()">Login</button>
    </form>
  </div>
</template>

<script>
import firebase from "firebase/compat/app";
import "firebase/compat/auth";
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    register() {
      try {
        firebase
          .auth()
          .createUserWithEmailAndPassword(this.email, this.password);

        alert("Successfully registered! Please login.");
        this.$router.push("/tutorial");
      } catch (error) {
        alert(error.message);
      }
    },
  },
};
</script>

<style scoped>
.container {
  margin-top: 6rem;
  display: flex;
  text-align: center;
  align-items: center;
  justify-content: center;
}

.container input {
  height: 2rem;
  width: 30rem;
}

.password {
  margin-top: 1.5rem;
}

button {
  margin-top: 1.5rem;
  width: 30.5rem;
  font-size: 18px;
  height: 2rem;
  background: rgb(40, 96, 217);
  color: white;
}

button:hover {
  background: blue;
}

h2 {
  font-size: 30px;
}
</style>
