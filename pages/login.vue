<template>
  <div>
    <navbar />
    <div
      class="h-3/4 w-3/4 mt-12 mx-auto flex flex-row rounded-xl bg-teal-600 drop-shadow-2xl"
    >
      <img
        class="h-full w-2/3 my-auto rounded-xl"
        src="../assets/images/signup.jpg"
        alt=""
      />
      <form
        class="flex flex-col h-96 w-96 justify-center my-auto gap-2 p-6"
        action=""
      >
        <h1 class="font-poppins text-5xl font-bold">Login</h1>
        <input
          class="rounded-md pl-2 py-2"
          type="text"
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
        <button
          class="h-12 text-xl py-2 font-poppins text-white bg-violet-700 rounded-lg hover:bg-violet-600 active:bg-violet-700 focus:outline-none focus:ring focus:ring-violet-200"
          @click.prevent="login"
        >
          Sign In
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
        email: "",
        password: "",
      },
    };
  },
  methods: {
    async login() {
      try {
        await fetch("http://localhost:1337/api/auth/local", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify({
            identifier: this.user.email,
            password: this.user.password,
          }),
        })
          .then((res) => res.json())
          .then((data) => {
            localStorage.setItem('token', data.jwt)
            setTimeout(this.$router.push("home"),1000)
        })
      } catch (error) {
      }
    },
  },
};
</script>
