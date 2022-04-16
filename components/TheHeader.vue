<template>
  <div class="navbar bg-red-500">
    <div class="flex-1">
      <NuxtLink to="/" class="btn btn-ghost uppercase text-xl text-white">
        Marvel Characters
      </NuxtLink>
    </div>
    <div class="flex-none gap-2">
      <div class="form-control">
        <input
          v-model="search"
          type="text"
          placeholder="Search characters"
          class="input input-bordered"
          @input="handleInput"
        >
      </div>
      <ul v-if=" searchQuery ">
        <li v-for="character in searchQuery" :key="character">
         <NuxtLink :to=" `/character/${character.id}` ">
            {{ character.name }}
         </NuxtLink>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
const PUBLIC_KEY = 'd3de654e788ba3ee07a6a7063415efd9'

export default {
  methods: {
    async handleInput () {
      if (this.searchQuery) {
        this.searchQuery = await axios.get('http://gateway.marvel.com/v1/public/characters', {
          params: {
            orderBy: 'name',
            limit: 8,
            nameStartsWith: this.search,
            apikey: PUBLIC_KEY
          }
        }).then((result) => {
          return result.data.data.results
        })
        console.log(this.searchQuery)
      }
    }
  },
  data () {
    return {
      searchQuery: []
    }
  }
}
</script>

<style scoped>
  .navbar {
    padding: 40px;
  }
</style>
