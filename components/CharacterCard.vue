<template>
  <div>
    <div class="card w-96 shadow-xl text-black">
      <NuxtLink :to="`/character/${characterItem.id}`">
        <figure>
          <img
            :src="`${characterItem.thumbnail.path}/landscape_medium.${characterItem.thumbnail.extension}`"
            alt="marvel"
          />
        </figure>
        <div class="card-body">
          <h2 class="card-title">
            {{ characterItem.name }}
          </h2>
          <p v-if="characterItem.description">
            {{ characterItem.description }}
          </p>
          <p v-else>No description found :(</p>
        </div>
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    characterItem: {
      type: Object,
      default: () => {},
    },
  },
};
</script>

<style scoped>
.card:hover {
  background-color: rgb(224, 149, 149);
}

.card {
  width: 92%;
  margin: 20px 20px 0 20px;
  min-height: 350px;
}

p {
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 4;
  -webkit-box-orient: vertical;
}

button {
  border: none;
}
</style>
