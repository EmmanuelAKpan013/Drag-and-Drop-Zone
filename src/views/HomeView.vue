<template>
  <div class="home-container">
    <div class="home">
      <h1>UPLOAD FILES</h1>
      <h3>Upload any document you want</h3>
      <DropZone @drop.prevent="drop" @change="selectedFile" />

      <div class="file-info">
        <!-- <div class="file-type">{{ dropzoneFile.type }}</div> -->
        <p v-for="(file, index) in dropzoneFile" :key="index">
          {{ file.name }}
        </p>
      </div>

      <button class="upload">Upload</button>
      <!-- <span class="file-info">
        File Type: {{ dropzoneFile.type }}
        <br />
        File: {{ dropzoneFile.name }}</span
      > -->
    </div>
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
      console.log(e.dataTransfer);
      dropzoneFile.value = e.dataTransfer.files;
      // const [first, second] = dropzoneFile.value
      console.log(dropzoneFile.value);
      console.log(dropzoneFile);

      // console.log(e.dataTransfer);
    };

    const selectedFile = () => {
      dropzoneFile.value = document.querySelector(".dropzonefile").files[0];
    };

    return { dropzoneFile, drop, selectedFile };
  },
};
</script>
<style lang="scss" scoped>
.home-container {
  background-color: rgb(116, 148, 236);
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 100vh;
}

.home {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 500px;
  background-color: #fafbfd;
  border-radius: 10px;

  h1 {
    color: rgb(193, 194, 196);
    font-size: 40px;
    margin-bottom: 3px;
  }

  h3 {
    margin: 5px 0 25px 0;
    color: rgb(193, 194, 196);
  }

  .file-info {
    display: flex;
    justify-content: center;
    align-items: center;
    column-gap: 20px;
    margin-top: 32px;

    .file-type {
      border-radius: 8px;
      padding: 20px;
      background: rgb(116, 148, 236);
      color: #fff;
    }
  }

  .upload {
    margin-top: 35px;
    border-radius: 10px;
    border: none;
    color: #fff;
    padding: 10px 20px;
    background: rgb(116, 148, 236);
  }

  .upload:hover {
    background: rgb(165, 176, 209);
  }
}
</style>
