<template>
  <div>
    <main>
      <ul class="container sm grid grid-cols-6">
        <li v-for="character in charactersList" :key="character">
          <CharacterCard :character-item=" character " />
        </li>
      </ul>

      <div class="container">
        <div class="btn-group place-content-center">
          <button class="btn btn-disabled">
            1
          </button>
          <button class="btn">
            2
          </button>
          <button class="btn">
            3
          </button>
          <button class="btn">
            4
          </button>
          <button class="btn">
            5
          </button>
        </div>
      </div>

      <!-- <NuxtLink :to="`/page/2`">
        <button class="btn center">Prox pagina</button>
      </NuxtLink> -->
    </main>
  </div>
</template>

<script>
export default {
  props: {
    charactersList: {
      type: Object,
      default: () => {}
    }
  }
}
</script>

<style scoped>
  .btn-group {
    margin: 10px 0;
  }
</style>
