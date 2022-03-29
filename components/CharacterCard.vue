<template>
  <div>
    <ul class="container sm grid grid-cols-4 gap-4">
      <li v-for="character in content" :key="character">
        <div class="card w-96 bg-base-100 shadow-xl">
          <figure><img :src=" character.thumbnail.path " alt="marvel"></figure>
          <div class="card-body">
            <h2 class="card-title">
              {{ character.name }}
            </h2>
            <p>
              {{ character.id }}
            </p>
            <div class="card-actions justify-end">
              <button class="btn btn-primary">
                More info
              </button>
            </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>
