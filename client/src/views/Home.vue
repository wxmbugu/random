<template>
  <div class="max-w-xs w-full m-auto bg-indigo-100 rounded p-5">
    <header>
      <img class="w-20 mx-auto mb-5" src="https://img.icons8.com/ultraviolet/240/000000/rebel.png" />
    </header>
    <form @submit.prevent="uploadmedia">
      <div>
        <label class="block mb-2 text-indigo-500">Media</label>
        <input v-on:change="onFileChange"
          class="w-full p-2 mb-6 text-indigo-700 border-b-2 border-indigo-500 outline-none focus:bg-gray-300" type="file"
          name="file" />
      </div>
      <div>
        <button class="w-full bg-indigo-700 hover:bg-pink-700 text-white font-bold py-2 px-4 mb-6 rounded" type="submit">
          Upload
        </button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      file: null,
    }
  },
  methods: {
    onFileChange(event) {
      this.file = event.target.files[0]
    },
    async uploadmedia() {
      console.log(this.file)
      const formData = new FormData()
      formData.append('myFile', this.file)
      try {
        await axios.post('http://localhost:9000/media', formData)
        this.getcontent()
      } catch (err) {
        console.log(err)
      }
    },
  },
}
</script>
