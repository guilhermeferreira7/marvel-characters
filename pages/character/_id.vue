<template>
  <div>
    <TheHeader />
    <main>
      <div>
        {{ character.name }}
        {{ character.description }}
      </div>
    </main>
    <TheFooter />
  </div>
</template>

<script>
import axios from 'axios'
const PUBLIC_KEY = 'd3de654e788ba3ee07a6a7063415efd9'

export default {
  async fetch () {
    const id = this.$route.params.id
    this.character = await axios.get('http://gateway.marvel.com/v1/public/characters', {
      params: {
        id,
        apikey: PUBLIC_KEY
      }
    }).then((result) => {
      return result.data.data.results[0]
    })
  },
  data () {
    return {
      character: []
    }
  }
}

</script>
