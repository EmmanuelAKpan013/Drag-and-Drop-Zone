<template>
  <div class="home">
    <h1>UPLOAD FILES</h1>
    <h3>Upload any document you want</h3>
    <DropZone @drop.prevent="drop" @change="selectedFile" />
    <span class="file-info">File: {{ dropzoneFile.name }}</span>
  </div>
</template>

<script>
import { ref } from "vue";
// @ is an alias to /src
import DropZone from "@/components/DropZone.vue";

export default {
  name: "HomeView",
  components: {
    DropZone,
  },
  setup() {
    let dropzoneFile = ref("");

    const drop = (e) => {
      dropzoneFile.value = e.dataTransfer.files[0];
    };

    const selectedFile = () => {
      dropzoneFile.value = document.querySelector(".dropzonefile").files[0];
    };

    return { dropzoneFile, drop, selectedFile };
  },
};
</script>
<style lang="scss" scoped>
.home {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: rgb(116, 148, 236);

  h1 {
    color: rgb(214, 218, 229);
    font-size: 40px;
    margin-bottom: 3px;
  }

  h3 {
    margin: 5px 0 25px 0;
    color: rgb(214, 218, 229);
  }

  .file-info {
    margin-top: 32px;
  }
}
</style>
