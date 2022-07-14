<template>
  <div>
    <HeaderPage />

    <main>
      <PageTitle title="All Characters" />

      <CharactersList :characters-list="characters" :pagination="pagination" />
    </main>
  </div>
</template>

<script>
import axios from "axios";
const PUBLIC_KEY = "d3de654e788ba3ee07a6a7063415efd9";
const limit = 4;

export default {
  name: "IndexPage",

  head() {
    return {
      title: "Marvel characters",
    };
  },

  data() {
    return {
      characters: [],
      pagination: {},
    };
  },

  async fetch() {
    const offset =
      this.$route.query && this.$route.query.page
        ? this.$route.query.page * limit - limit
        : 0;

    this.pagination = {
      lastPage: 300,
    };

    this.characters = await axios
      .get("http://gateway.marvel.com/v1/public/characters", {
        params: {
          orderBy: "name",
          limit,
          offset,
          apikey: PUBLIC_KEY,
        },
      })
      .then((result) => {
        return result.data.data.results;
      });
  },

  watch: {
    "$route.query": "$fetch",
  },
};
</script>
