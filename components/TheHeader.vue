<template>
  <div class="navbar bg-base-100">
    <div class="flex-1">
      <NuxtLink to="/" class="btn btn-ghost uppercase text-xl">Marvel Characters</NuxtLink>
    </div>
    <div class="flex-none gap-2">
      <div class="form-control">
        <input type="text" placeholder="Search" class="input input-bordered">
      </div>
    </div>
  </div>
</template>

<style scoped>
  .navbar {
    padding: 40px;
  }
</style>
