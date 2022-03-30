<template>
  <div>
    <TheHeader />

    <ul class="container sm grid grid-cols-4 gap-4">
      <li v-for="character in characters" :key="character">
        <CharacterCard :character-item=" character " />
      </li>
    </ul>

    <TheFooter />
  </div>
</template>

<script>
import axios from 'axios'

const PUBLIC_KEY = 'd3de654e788ba3ee07a6a7063415efd9'
const apiData = []

async function getCharacters () {
  await axios.get(`http://gateway.marvel.com/v1/public/characters?apikey=${PUBLIC_KEY}`).then((result) => {
    result.data.data.results.forEach((item) => {
      apiData.push(item)
    })
  })
}
getCharacters()

export default {
  name: 'IndexPage',
  asyncData () {
    return {
      characters: apiData
    }
  }
}
</script>
