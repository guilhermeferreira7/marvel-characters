<template>
  <div>
    <TheHeader />

    <main>
      <CharactersList :characters-list=" characters " />
    </main>

    <TheFooter />
  </div>
</template>

<script>
import axios from 'axios'
const PUBLIC_KEY = 'd3de654e788ba3ee07a6a7063415efd9'
const apiData = []

//  total characters = 1600
async function getCharacters () {
  await axios.get(`http://gateway.marvel.com/v1/public/characters?orderBy=name&limit=6&offset=1200&apikey=${PUBLIC_KEY}`).then((result) => {
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
