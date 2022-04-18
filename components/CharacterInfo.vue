<template>
  <div>
    <div class="grid grid-cols-12 container text-black character-container">
      <div class="col-start-1 col-end-4">
        <h2 id="character-name" class="text-center text-black text-2xl font-bold">
          {{ character.name }}
        </h2>
        <figure class="flex justify-center">
          <img
            :src="
              `${character.imgPath}/portrait_incredible.${character.imgExtension}`
            "
            alt="marvel"
            class=""
          >
        </figure>
        <div class="text-center">
          <a :href=" character.bioUrl " target="_blank">
            <button class="btn bio-button bg-red-500 text-white">
              Official page
            </button>
          </a>
        </div>
      </div>
      <div class="col-start-4 col-end-13 character-desc-container">
        <p v-if="character.description" class="text-lg">
          <span class="font-bold">
            Description:
          </span>
          {{ character.description }}
        </p>
        <p v-else class="text-2xl">
          <span class="font-bold">
            Description:
          </span>
          Description No description found :(
        </p>
        <p class="text-center text-2xl font-bold margin-top">
          Appears in:
        </p>
        <div class="grid grid-cols-3 container margin-top">
          <div v-for="comic in comics" :key="comic">
            <figure class="flex justify-center">
              <img
                :src="`${comic.imgPath}/portrait_xlarge.${comic.imgExtension}`"
                alt="comic"
              >
            </figure>
            <h4 class="text-center text-lg font-bold">
              {{ comic.title }}
            </h4>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    character: {
      type: Object,
      default: () => {}
    },
    comics: {
      type: Array,
      default: () => {}
    }
  }
}
</script>

<style scoped>
  .character-container {
    min-height: 460px;
    margin-top: 20px;
    margin-bottom: 10px;
  }

  #character-name {
    padding: 5px 0;
  }

  .bio-button {
    margin-top: 10px;
    border: none;
  }

  .character-desc-container {
    padding-left: 15px;
  }

  .margin-top {
    margin-top: 10px;
  }

</style>
