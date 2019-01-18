<template>
  <div>
    <ul class="gifs">
      <li v-for="gif in gifs">
        <a :href="gif.url" target="_blank"><img :src="gif.images.original.url" alt="" /></a>
      </li>
    </ul>
  </div>
</template>

<script>
  export default{
    props: ['gifs']
  }
</script>
