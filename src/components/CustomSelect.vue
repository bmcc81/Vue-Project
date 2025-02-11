<template>
  <div>
    <div v-bind="getRootProps()">
      <input v-bind="getInputProps()" />
      <p v-if="isDragActive">Drop the files here ...</p>
      <p v-else>Drag 'n' drop some files here, or click to select files</p>
    </div>
    <button @click="open">open</button>
  </div>
  <div class="showJson"></div>
</template>

<script lang="ts">
import { useDropzone } from 'vue3-dropzone'

export default {
  name: 'UseDropzoneDemo',
  setup() {
    function onDrop(acceptFiles, rejectReasons) {
      console.log(acceptFiles)
      console.log(JSON.stringify(acceptFiles))

      console.log(rejectReasons)
    }

    const { getRootProps, getInputProps, ...rest } = useDropzone({ onDrop })

    return {
      getRootProps,
      getInputProps,
      ...rest,
    }
  },
}
</script>
