<template>
  <br />
  <div class="w-full m-auto p-5 max-w-3xl rounded bg-indigo-100">
    <form @submit.prevent="Register">
      <div class="grid md:grid-cols-2 sm:grid-cols-1 gap-4">
        <div>
          <label class="block mb-2 text-indigo-500">FirstName</label>
          <input v-model="Firstname"
            class="w-full p-2 mb-6 text-indigo-700 border-b-2 border-indigo-500 outline-none focus:bg-gray-300"
            type="text" name="firstname" />
        </div>
        <div>
          <label class="block mb-2 text-indigo-500">Address</label>
          <input v-model="Address"
            class="w-full p-2 mb-6 text-indigo-700 border-b-2 border-indigo-500 outline-none focus:bg-gray-300"
            type="text" name="address" />
        </div>
        <div>
          <label class="block mb-2 text-indigo-500">Email</label>
          <input v-model="Email"
            class="w-full p-2 mb-6 text-indigo-700 border-b-2 border-indigo-500 outline-none focus:bg-gray-300"
            type="email" name="email" />
        </div>
        <div>
          <label class="block mb-2 text-indigo-500">Password</label>
          <input v-model="Password"
            class="w-full p-2 mb-6 text-indigo-700 border-b-2 border-indigo-500 outline-none focus:bg-gray-300"
            type="password" name="password" />
        </div>
        <div>
          <label class="block mb-2 text-indigo-500">Confirm Password</label>
          <input v-model="CPassword"
            class="w-full p-2 mb-6 text-indigo-700 border-b-2 border-indigo-500 outline-none focus:bg-gray-300"
            type="password" name="cpassword" />
        </div>
      </div>
      <div>
        <button class="w-full bg-indigo-700 hover:bg-pink-700 text-white font-bold py-2 px-4 mb-6 rounded" type="submit"
          name="submit">
          Register
        </button>
        <p class="text-red-700">{{ error }}</p>
      </div>
      <footer>
        <router-link :to="{ name: 'Login' }" class="text-indigo-700 hover:text-pink-700 text-sm float-right" href="#">Have
          an account?Login</router-link>
      </footer>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      Firstname: '',
      Email: '',
      Password: '',
      CPassword: '',
      error: null,
    }
  },
  methods: {
    Register() {
      this.$store
        .dispatch('register', {
          first_name: this.Firstname,
          email: this.Email,
          password: this.Password,
          re_password: this.CPassword,
          hesquserrole: 0,
        })
        .then(() => {
          this.$router.push({ name: 'Login' })
        })
        .catch((err) => {
          this.error = err.response.data
        })
    },
  },
}
</script>
