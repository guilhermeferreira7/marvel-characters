<template>
  <div>
    <div class="card w-96 shadow-xl bg-red-300 text-black">
      <figure><img :src=" `${characterItem.thumbnail.path}/landscape_medium.${characterItem.thumbnail.extension}` " alt="marvel"></figure>
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
        <div class="card-actions justify-end">
          <NuxtLink :to=" `/character/${characterItem.id}`  ">
            <button class="btn bg-red-500 text-black">
              More info
            </button>
          </NuxtLink>
        </div>
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
    width: 92%;
    margin: 20px 20px 0 20px;
    min-height: 340px;
  }

  p {
    max-width: 30ch;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  button {
    border: none;
  }
</style>
