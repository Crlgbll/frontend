<template>
  <div class="h-14 w-full bg-teal-300/80 flex justify-around">
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
    <div class="h-14 w-1/4 items-center font-bold">
      <ul class="flex py-3 justify-around text-lg items-center">
        <div class="h-10 w-70 justify-between space-x-2">
          <nuxt-link to="home">
            <button class="hover:text-violet-700 duration-300">
              <li>Home</li>
            </button>
          </nuxt-link>
          <nuxt-link to="bookmark"> 
            <button class="hover:text-violet-700 duration-300">
              <li>Bookmark</li>
            </button>
          </nuxt-link>
          <nuxt-link to="profile">
            <button class="hover:text-violet-700 duration-300">
              <li>Profile</li>
            </button>
          </nuxt-link>
          <nuxt-link to="login">
            <button
              @click="userLogout"
              class="hover:text-violet-700 duration-300 border-2 border-violet-500 outline-2 rounded-md px-2"
            >
              <li>Logout</li>
            </button> 
          </nuxt-link>
        </div>
      </ul>
    </div>
  </div>
</template>
<script lang="js">

// export default {
//   userLogout() {
//       localStorage.removeItem("token")
//       this.$router.push("/")
//     }
// }
export default {
  data() {
    return {
      // data properties here
      
    }
  },
  methods: {
    userLogout() {
      // method logic here
      localStorage.removeItem("token")
      this.$router.push("/")
    }
  }
}

</script>
