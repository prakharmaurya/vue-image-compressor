<template>
  <div id="app">
    <p v-if="!hasImage">Loading....</p>
    <image-compressor
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
    </image-compressor>
  </div>
</template>

<script>
import ImageCompressor from "./components/ImageCompressor.vue";

export default {
  name: "app",
  components: {
    ImageCompressor,
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
