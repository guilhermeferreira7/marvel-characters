<template>
  <div>
    <!-- <div>{{ characterItem }}</div> -->
    <div class="card w-96 bg-base-100 shadow-xl">
      <figure><img :src=" characterItem.thumbnail.path + '/standard_large.jpg' " alt="marvel"></figure>
      <div class="card-body">
        <h2 class="card-title">
          {{ characterItem.name }}
        </h2>
        <p v-if=" characterItem.description ">
          {{ characterItem.description }}
        </p>
        <p v-else>
          No description found :(
        </p>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    characterItem: {
      type: Object,
      default: () => {}
    }
  }
}
</script>

<style scoped>
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
