<template>
  <div>
    <TheHeader />

    <main>
      <CharactersList :characters-list=" characters " :pagination=" pagination " />
    </main>

    <TheFooter />
  </div>
</template>

<script>
import axios from 'axios'
const PUBLIC_KEY = 'd3de654e788ba3ee07a6a7063415efd9'

export default {
  name: 'IndexPage',
  async fetch () {
    const offset = this.$route.query && this.$route.query.page ? (this.$route.query.page * 6) - 6 : 0

    this.pagination = {
      lastPage: 261
    }

    this.characters = await axios.get('http://gateway.marvel.com/v1/public/characters', {
      params: {
        orderBy: 'name',
        limit: 6,
        offset,
        apikey: PUBLIC_KEY
      }
    }).then((result) => {
      return result.data.data.results
    })
  },
  data () {
    return {
      characters: [],
      pagination: {}
    }
  },
  watch: {
    '$route.query': '$fetch'
  }
}
</script>
