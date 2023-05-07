<template>
  <div
    class="h-14 w-full bg-green-300 flex justify-around items-center px-2 md:px-6 lg:px-10"
  >
    <nuxt-link to="/">
      <div class="h-14 w-60 flex items-center">
        <img
          class="h-14 w-14"
          src="../assets/images/recipedia-logo.png"
          alt=""
        />
        <h1 class="font-pops text-2xl font-bold">
          <span class="text-blue-700">RECIPE</span>DIA
        </h1>
      </div>
    </nuxt-link>
    <div class="h-14 w-full md:w-1/2 items-center font-bold">
      <ul class="flex py-3 justify-around text-lg items-center">
        <div class="h-10 w-70 md:w-96 justify-between space-x-2">
          <nuxt-link to="/">
            <button class="hover:text-violet-700 duration-300">
              <li>Home</li>
            </button>
          </nuxt-link>
          <nuxt-link to="/">
            <button class="hover:text-violet-700 duration-300">
              <li>Bookmark</li>
            </button>
          </nuxt-link>
          <nuxt-link to="login">
            <button class="hover:text-violet-700 duration-300">
              <li>Login</li>
            </button>
          </nuxt-link>
          <nuxt-link to="signup">
            <button
              class="hover:text-violet-700 duration-300 border-2 border-violet-500 outline-2 rounded-md px-2"
            >
              <li>Sign Up</li>
            </button>
          </nuxt-link>
        </div>
      </ul>
    </div>
  </div>
</template>

<script>

</script>