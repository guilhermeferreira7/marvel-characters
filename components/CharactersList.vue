<template>
  <div>
    <main>
      <ul class="container sm grid grid-cols-2 lg:grid-cols-6">
        <li v-for="character in charactersList" :key="character">
          <CharacterCard :character-item=" character " />
        </li>
      </ul>

      <div class="container">
        <div class="btn-group place-content-center">
          <button class="btn bg-red-500 text-white" :class=" currentPage == '1' ? 'bg-red-400 btn-disabled' : '' " @click="changePage(1)">
            First page
          </button>
          <button class="btn bg-red-500 text-white" :class=" currentPage == '1' ? 'bg-red-400 btn-disabled' : '' " @click="changePage(currentPage - 1)">
            «
          </button>
          <button class="btn btn-disabled bg-red-400 text-white">
            Page {{ currentPage }}
          </button>
          <button class="btn bg-red-500 text-white" :class=" currentPage == pagination.lastPage ? 'bg-red-400 btn-disabled' : '' " @click="changePage(currentPage + 1)">
            »
          </button>
          <button class="btn bg-red-500 text-white" :class=" currentPage == pagination.lastPage ? 'bg-red-400 btn-disabled' : '' " @click="changePage(pagination.lastPage)">
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
  data () {
    return {
      currentPage: 1
    }
  },
  methods: {
    changePage (page) {
      this.currentPage = page
      this.$router.replace({ query: { page } })
    }
  }
}
</script>

<style scoped>
  .btn-group {
    margin: 10px 0;
  }
</style>
