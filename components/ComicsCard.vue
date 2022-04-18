<template>
  <div>
    <ul>
      <li v-for="comic in comics" :key="comic">
        {{ comic.title }}
        <figure>
          <img
            :src=" `${comic.images[0].path}/landscape_medium.${comic.images[0].extension}` "
            alt="marvel character"
          >
        </figure>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    comics: {
      type: Array,
      default: () => {}
    }
  }
}
</script>

<style>

</style>
