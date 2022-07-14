<template>
  <div>
    <HeaderPage />

    <main>
      <PageTitle title="Character Info" />
      <CharacterInfo :character="character" :comics="comics" />
    </main>
  </div>
</template>

<script>
import axios from "axios";
const PUBLIC_KEY = "d3de654e788ba3ee07a6a7063415efd9";

export default {
  head() {
    return {
      title: this.character.name,
    };
  },

  data() {
    return {
      character: {},
      comics: [],
    };
  },

  async fetch() {
    const id = this.$route.params.id;
    const characterData = await axios
      .get("http://gateway.marvel.com/v1/public/characters", {
        params: {
          id,
          apikey: PUBLIC_KEY,
        },
      })
      .then((result) => {
        return result.data.data.results[0];
      });

    const bioUrl = characterData.urls[0].url;

    this.character = {
      name: characterData.name,
      description: characterData.description,
      imgPath: characterData.thumbnail.path,
      imgExtension: characterData.thumbnail.extension,
      bioUrl,
    };

    const comicsData = await axios
      .get(`http://gateway.marvel.com/v1/public/characters/${id}/comics`, {
        params: {
          apikey: PUBLIC_KEY,
          limit: 6,
        },
      })
      .then((result) => {
        return result.data.data.results;
      });

    this.comics = [];

    comicsData.forEach((element) => {
      this.comics.push({
        imgPath: element.thumbnail.path,
        imgExtension: element.thumbnail.extension,
        title: element.title,
        url: element.urls[0].url,
      });
    });
  },
};
</script>
