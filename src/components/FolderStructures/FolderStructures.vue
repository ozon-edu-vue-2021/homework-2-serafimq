<template>
 <div>
   <Folder
      v-for="(folder, index) in folders"
      :folder="folder"
      :key="index"
   />
 </div>
</template>

<script>
import Folder from '../Folder/Folder.vue'
import structures from '../../../public/static/node_modules2.json'

export default {
  name: 'ForlderStructures',
  components: {
    Folder
  },
  data() {
    return {
        folders: [structures],
    }
  },
}
</script>

<style>

</style>
