<template>
  <div>
    <HeaderPage />

    <main>
      <div>
        <ul>
          <li v-for="comic in comics" :key="comic">
            {{ comic.title }}
            <figure>
              <img
                :src=" `${comic.images[0].path}/landscape_medium.${comic.images[0].extension}` "
                alt="marvel character"
              >
            </figure>
          </li>
        </ul>
      </div>
    </main>

    <FooterPage />
  </div>
</template>

<script>
import axios from 'axios'
const PUBLIC_KEY = 'd3de654e788ba3ee07a6a7063415efd9'

export default {
  data () {
    return {
      character: [],
      comics: []
    }
  },

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

    this.comics = await axios.get(`http://gateway.marvel.com/v1/public/characters/${id}/comics`, {
      params: {
        apikey: PUBLIC_KEY,
        limit: 3
      }
    }).then((result) => {
      return result.data.data.results
    })
  }
}

</script>
