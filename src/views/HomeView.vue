<template>
  <div class="home-container">
    <div class="home">
      <h1>UPLOAD FILES</h1>
      <h3>Upload any document you want</h3>
      <DropZone @drop.prevent="drop" @change="selectedFile" />

      <div class="file-info">
        <ul v-for="(file, index) in dropzoneFile" :key="index">
          <li>
            <div class="file-type">{{ file.type }}</div>
            <div class="file-name">
              {{ file.name }}
            </div>
          </li>
        </ul>
      </div>

      <button class="upload">Upload</button>
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
      console.log(dropzoneFile.value);
      console.log(dropzoneFile);
    };

    const selectedFile = () => {
      dropzoneFile.value = document.querySelector(".dropzonefile").files;
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
  min-height: 500px;
  max-height: 800px;
  background-color: #fafbfd;
  border-radius: 10px;

  h1 {
    color: rgb(193, 194, 196);
    font-size: 40px;
    margin: 20px 0 3px 0;
  }

  h3 {
    margin: 5px 0 25px 0;
    color: rgb(193, 194, 196);
  }

  .file-info {
    align-items: center;
    margin-top: 32px;

    ul {
      display: flex;
      flex-direction: column;
      row-gap: 10px;
      list-style: none;

      li {
        display: flex;
        column-gap: 20px;
        margin: 8px 0;

        .file-type {
          border-radius: 8px;
          padding: 10px;
          background: rgb(116, 148, 236);
          color: #fff;
        }

        .file-name {
          display: flex;
          justify-content: center;
          align-items: center;
        }
      }
    }
  }

  .upload {
    margin: 25px 0 20px 0;
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
