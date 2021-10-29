<template>
 <div
  :class="activeElementClass"
  @click.stop="showContent"
>
   <template v-if="folder.type === 'directory'"> <folder-icon /> </template>
   <template v-if="folder.type === 'file'"> <file-icon />  </template>
   <template v-if="folder.type === 'link'"> <link-icon />  </template>
   <div> {{ folder.name }} 
     <template v-if="folder.type === 'link'"> <a href="#"> - {{ folder.target }}</a></template>
   </div>
   <div
    :class="contentClasses"
   >
    <Folder
        v-for="(childFolder, subIndex) in folder.contents"
        v-bind:folder="childFolder"
        :index="subIndex"
        :key="subIndex"
        :parentFolder="folder"
    />
   </div>
 </div>
</template>

<script>
import FileIcon from '../Icons/FileIcon.vue'
import FolderIcon from '../Icons/FolderIcon.vue'
import LinkIcon from '../Icons/LinkIcon.vue'

export default {
  name: 'Folder',
  components: { FolderIcon, FileIcon, LinkIcon },
  props: {
    folder: {
      type: Object,
      required: true,
    },
    parentFolder: {
      required: false,
    },
  },
  data() {
    return {
      isOpenContent: false,
      isActiveElement: false,
    }
  },
  computed: {
    contentClasses() {
      return ['folder-content', {
          'folder-content_open' : this.isOpenContent,
        }];
    },
    activeElementClass() {
      return ['folder', {
          'active-element' : this.isActiveElement,
        }];
    },
  },
  methods: {
    showContent() {
      this.isOpenContent = !this.isOpenContent;
      if (this.folder.type !== 'directory') {
          this.isActiveElement = !this.isActiveElement;
      }
    },
  },
}
</script>

<style scoped>
  .folder {
    display: flex;
    flex-direction: column;
  }
  .folder-content {
    padding-left: 50px;
    display: none;
  }

  .folder-content_open {
    display: block;
  }

  .active-element {
    color: red;
  }
</style>
