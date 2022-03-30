<template>
  <div>
    <TheHeader />

    <main>
      <ul class="container sm grid grid-cols-5">
        <li v-for="character in characters" :key="character">
          <CharacterCard :character-item=" character " />
        </li>
      </ul>
    </main>

    <TheFooter />
  </div>
</template>

<script>
import axios from 'axios'
const PUBLIC_KEY = 'd3de654e788ba3ee07a6a7063415efd9'
const apiData = []

async function getCharacters () {
  await axios.get(`http://gateway.marvel.com/v1/public/characters?orderBy=-modified&limit=100&apikey=${PUBLIC_KEY}`).then((result) => {
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
