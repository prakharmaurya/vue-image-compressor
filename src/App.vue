<template>
  <div id="app">
    <p v-if="!hasImage">Loading....</p>
    <image-uploader
      :preview="true"
      :sizeTo="200"
      :capture="false"
      :debug="1"
      doNotResize="gif"
      :autoRotate="false"
      outputFormat="verbose"
      @doneCompression="setImage"
    >
      <label for="fileInput" slot="upload-label">
        <span class="upload-caption">{{
          hasImage ? "Replace" : "Upload"
        }}</span>
      </label>
    </image-uploader>
  </div>
</template>

<script>
import ImageUploader from "./components/ImageUploader.vue";

export default {
  name: "app",
  components: {
    ImageUploader,
  },
  data() {
    return { hasImage: false };
  },
  methods: {
    setImage: function(output) {
      this.hasImage = true;
      this.image = output;
    },
  },
};
</script>
