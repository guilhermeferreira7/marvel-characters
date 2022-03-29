<template>
  <div>
    <TheHeader />

    <ul class="container sm grid grid-cols-4 gap-4">
      <li v-for="character in content" :key="character">
        <div class="card w-96 bg-base-100 shadow-xl">
          <figure><img :src=" character.thumbnail.path + '/standard_large.jpg' " alt="marvel"></figure>
          <div class="card-body">
            <h2 class="card-title">
              {{ character.name }}
            </h2>
            <p v-if=" character.description ">
              {{ character.description }}
            </p>
            <p v-else>
              No description found :(
            </p>
          </div>
        </div>
      </li>
    </ul>

    <!-- <CharacterCard /> -->

    <TheFooter />
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

export default {
  name: 'IndexPage',
  asyncData () {
    return {
      content: characters
    }
  }
}
</script>

<style>
  .card {
    width: 80%;
  }

  p {
    max-width: 50ch;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
</style>
