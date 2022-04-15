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
          <button class="btn" @click="changePage(1)">
            First page
          </button>
          <button class="btn" @click="prevPage()">
            «
          </button>
          <button class="btn">
            Page {{ currentPage }}
          </button>
          <button class="btn" @click="nextPage()">
            »
          </button>
          <button class="btn" @click="changePage(pagination.lastPage)">
            Last page
          </button>
        </div>
      </div>
      
    </main>
  </div>
</template>

<script>
export default {
  props: {
    charactersList: {
      type: Array,
      default: () => {}
    },
    pagination: {
      type: Object,
      default: () => {}
    }
  },
  methods: {
    nextPage () {
      this.currentPage++
      const page = this.currentPage
      this.$router.replace({ query: { page } })
    },
    prevPage () {
      this.currentPage--
      const page = this.currentPage
      this.$router.replace({ query: { page } })
    },
    changePage (page) {
      this.currentPage = page
      this.$router.replace({ query: { page } })
    }
  },
  data () {
    return {
      currentPage: 1
    }
  }
}
</script>

<style scoped>
  .btn-group {
    margin: 10px 0;
  }
</style>
