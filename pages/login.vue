<template>
  <div class="bg-stone-300 ">
    <navbar />
    <div class="flex flex-col md:flex-row justify-center items-center h-screen">
      <img
        class="w-full md:w-2/3 h-60 md:h-full md:rounded-l-xl"
        src="../assets/images/signup.jpg"
        alt=""
      />
      <form
        class="w-full md:w-1/3 h-full flex flex-col justify-center gap-4 p-6"
        @submit.prevent="login"
      >
        <h1
          class="font-poppins text-5xl font-bold text-center md:text-left md:mt-6"
        >
          Login
        </h1>
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
          type="submit"
          class="h-12 text-xl py-2 font-poppins text-white bg-violet-700 rounded-lg hover:bg-violet-600 active:bg-violet-700 focus:outline-none focus:ring focus:ring-violet-200"
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
        const response = await fetch("http://localhost:1337/api/auth/local", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify({
            identifier: this.user.email,
            password: this.user.password,
          }),
        });
        if (response.ok) {
          const data = await response.json();
          localStorage.setItem("token", data.jwt);
          this.$router.push("home");
        } else {
          alert("Wrong email or password");
        }
      } catch (error) {
        console.log(error);
        alert("An error occurred. Please try again.");
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
@media only screen and (max-width: 767px) {
  .h-screen {
    height: 100%;
  }
  .flex-col {
    flex-direction: column;
  }
  .md:flex-row {
    flex-direction: column;
  }
  .md:rounded-l-xl {
    border-radius: 0;
    border-top-left-radius: 10px;
  }
  img {
    width: 100%;
    height: auto;
    margin-bottom: 1rem;
  }
  form {
    width: 100%;
    max-width: 300px;
    margin: auto;
  }
}
</style>
