<template>
  <div>
    <header class="navbar bg-red-500 grid grid-cols-3">
      <div class="">
        <NuxtLink to="/" class="btn btn-ghost uppercase text-xl text-white">
          Marvel Characters
        </NuxtLink>
      </div>

      <div class="col-start-4 float-right">
        <div class="form-control">
          <input
            v-model="search"
            type="text"
            placeholder="Search characters"
            class="input input-bordered"
            @input="handleInput"
          >
        </div>
        <ul class="absolute overflow-auto text-black divide-y z-10 bg-white search-box">
          <li v-for="character in searchQuery" :key="character">
            <NuxtLink :to=" `/character/${character.id}` ">
              {{ character.name }}
            </NuxtLink>
          </li>
        </ul>

      </div>
    </header>
  </div>
</template>

<script>
import axios from 'axios'
const PUBLIC_KEY = 'd3de654e788ba3ee07a6a7063415efd9'

export default {
  data () {
    return {
      searchQuery: []
    }
  },

  methods: {
    handleInput () {
      this.searchCharacters()
    },

    async searchCharacters () {
      this.searchQuery = await axios.get('http://gateway.marvel.com/v1/public/characters', {
        params: {
          orderBy: 'name',
          limit: 100,
          nameStartsWith: this.search,
          apikey: PUBLIC_KEY
        }
      }).then((result) => {
        return result.data.data.results
      })
    }
  }
}
</script>

<style scoped>
  .navbar {
    padding: 40px;
  }

  .search-box {
    right: 32x;
    top: 85px;
    max-height: 300px;
    width: 195px;
  }

</style>
