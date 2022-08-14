<template>
  <div
    @dragenter.prevent="toggleActive"
    @dragleave.prevent="toggleActive"
    @dragover.prevent
    @drop.prevent="toggleActive"
    :class="{ 'active-dropzone': active }"
    class="dropzone"
  >
    <img src="../assets/cloud.png" alt="" />
    <span>Drag & Drop your files here</span>
    <span>OR</span>
    <label for="dropzonefile">Browse Files</label>
    <input multiple type="file" id="dropzonefile" class="dropzonefile" />
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "DropZone",
  setup() {
    const active = ref(false);

    const toggleActive = () => {
      active.value = !active.value;
    };

    return {
      active,
      toggleActive,
    };
  },
};
</script>

<style scoped lang="scss">
.dropzone {
  width: 400px;
  height: 200px;
  margin: 0 30px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 16px;
  border: 2px dashed #b3b3b4;
  background: rgb(235, 235, 245);
  transition: 0.3s ease all;

  img {
    width: 50px;
    height: 50px;
  }

  span {
    color: rgb(170, 179, 209);
    font-weight: 700;
  }

  label {
    padding: 8px 12px;
    border-radius: 8px;
    color: #fff;
    background-color: rgb(88, 116, 198);
    transition: 0.3s ease all;
  }

  input {
    display: none;
  }
}

.active-dropzone {
  color: #fff;
  border-color: #fff;
  background-color: rgb(116, 148, 236);

  label {
    background-color: #fff;
    color: rgb(116, 148, 236);
  }
}
</style>
