<template>
  <div>
    <!-- <TheHeader /> -->
    <!-- <NuxtLink to="/character">
      Characters
    </NuxtLink> -->
    <!-- <ul> -->
    <ul class="container sm grid grid-cols-4 gap-4">
      <li v-for="character in content" :key="character">
        <div class="card w-96 bg-base-100 shadow-xl">
          <figure><img :src=" character.thumbnail.path " alt="marvel" /></figure>
          <div class="card-body">
            <h2 class="card-title">
              {{ character.name }}
            </h2>
            <p>
              {{ character.description }}
            </p>
            <div class="card-actions justify-end">
              <button class="btn btn-primary">
                Buy Now
              </button>
            </div>
          </div>
        </div>
      </li>
    </ul>
    <!-- <TheFooter /> -->
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
// console.log(characters)

export default {
  name: 'IndexPage',
  asyncData () {
    return { content: characters }
  }
}
</script>

<style>
  .card {
    width: 80%;
  }
</style>
