<template>
    <div>
      <navbar />
      <div class="h-3/4 w-3/4 mt-12 mx-auto flex flex-row rounded-xl bg-teal-600 drop-shadow-2xl">
        <img class="h-full w-2/3 my-auto rounded-xl" src="../assets/images/signup.jpg" alt="" />
        <form class="flex flex-col h-96 w-96 justify-center my-auto gap-2 p-6" @submit.prevent="signup">
          <h1 class="font-poppins text-5xl font-bold">Sign-Up</h1>
          <input class="rounded-md pl-2 py-2" type="text" placeholder="Username" required v-model="user.username" />
          <input class="rounded-md pl-2 py-2" type="email" placeholder="Email" required v-model="user.email" />
          <input class="rounded-md pl-2 py-2" type="password" placeholder="Password" required v-model="user.password" />
          <input class="rounded-md pl-2 py-2" type="password" placeholder="Confirm Password" required />
          <button type="submit" class="h-12 text-xl py-2 font-poppins text-white bg-violet-700 rounded-lg hover:bg-violet-600 active:bg-violet-700 focus:outline-none focus:ring focus:ring-violet-200">
            Sign Up
          </button>
        </form>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        user: {
          username: '',
          email: '',
          password: '',
        },
      };
    },
    methods: {
      async signup() {
        try {
          const response = await fetch('http://localhost:1337/api/auth/local/register', {
            method: 'POST',
            headers: {
              'Content-Type': 'application/json',
            },
            body: JSON.stringify({
              username: this.user.username,
              email: this.user.email,
              password: this.user.password,
            })
          }).then(() => this.$router.push("login"))
          const data = await response.json();
          console.log(data);
        } catch (error) {
          console.error(error);
        }
      },
    },
  };
  </script>
  