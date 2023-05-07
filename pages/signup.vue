<template>
  <div class="bg-stone-300">
    <navbar />
    <div class="flex flex-col md:flex-row justify-center items-center h-screen">
      <img
        class="w-full md:w-2/3 h-60 md:h-full md:rounded-l-xl"
        src="../assets/images/signup.jpg"
        alt=""
      />
      <form
        class="w-full md:w-1/3 h-full flex flex-col justify-center gap-4 p-6"
        @submit.prevent="signup"
      >
        <h1
          class="font-poppins text-5xl font-bold text-center md:text-left md:mt-6"
        >
          Sign-Up
        </h1>
        <input
          class="rounded-md pl-2 py-2"
          type="text"
          placeholder="Username"
          required
          v-model="user.username"
        />
        <input
          class="rounded-md pl-2 py-2"
          type="email"
          placeholder="Email"
          required
          v-model="user.email"
        />
        <input
          class="rounded-md pl-2 py-2"
          type="password"
          placeholder="Password"
          required
          v-model="user.password"
        />
        <input
          class="rounded-md pl-2 py-2"
          type="password"
          placeholder="Confirm Password"
          required
        />
        <button
          type="submit"
          class="h-12 text-xl py-2 font-poppins text-white bg-violet-700 rounded-lg hover:bg-violet-600 active:bg-violet-700 focus:outline-none focus:ring focus:ring-violet-200"
        >
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
        username: "",
        email: "",
        password: "",
      },
    };
  },
  methods: {
    async signup() {
      try {
        const response = await fetch(
          "http://localhost:1337/api/auth/local/register",
          {
            method: "POST",
            headers: {
              "Content-Type": "application/json",
            },
            body: JSON.stringify({
              username: this.user.username,
              email: this.user.email,
              password: this.user.password,
            }),
          }
        ).then(() => this.$router.push("login"));
        const data = await response.json();
        console.log(data);
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style>
@media only screen and (min-width: 768px) {
  .h-screen {
    height: calc(100vh - 4rem);
  }
  form {
    max-width: 400px;
  }
}
</style>
