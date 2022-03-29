<template>
  <div>
    <NuxtLink to="/character">
      Characters
    </NuxtLink>

    <ul>
      <li v-for="(character, index) in characters" :key="index">
        {{ character }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

const PUBLIC_KEY = 'd3de654e788ba3ee07a6a7063415efd9'
const characters = []

async function getCharacters () {
  await axios.get(`http://gateway.marvel.com/v1/public/characters?apikey=${PUBLIC_KEY}`).then((result) => {
    result.data.data.results.forEach((item) => {
      characters.push(item)
    })
  })
}

getCharacters()

// const charExample = items[0]
console.log(characters)

export default {
  name: 'IndexPage'
}
</script>
