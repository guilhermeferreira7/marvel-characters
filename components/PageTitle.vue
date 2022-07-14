<template>
  <div>
    <div id="title">
      <h1 class="text-center text-black font-bold">
        {{ title }}
      </h1>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: "",
    },
  },
};
</script>

<style scoped>
#title h1 {
  font-size: 28px;
}

#title {
  margin: 10px 0;
}
</style>
