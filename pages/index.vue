<template>
  <div class='index'>
    <Dvd />
  </div>
</template>

<script>
import Dvd from '~/components/Dvd.vue'

export default {
  components: {
    Dvd
  }
}
</script>

<style>
html,body,svg{
    width: 100%;
    height: 100%;
    display: block;
    margin:0;
    padding: 0;
}
</style>
