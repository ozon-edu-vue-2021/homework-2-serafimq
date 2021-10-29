<template>
  <div id="app">
    <folder-structures/>
  </div>
</template>

<script>
    import FolderStructures from '@/components/FolderStructures/FolderStructures.vue';

    export default {
        name: 'App',
        components: {
            FolderStructures,
        }
    }
</script>

<style>
  html {
    background: #979696;
    color: beige;
  }
  #app {
    margin: 50px 100px;
  }
</style>
