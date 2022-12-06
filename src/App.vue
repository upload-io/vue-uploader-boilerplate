<template>
  <UploadDropzone :uploader="uploader"
                  :options="options"
                  :on-update="onFileUploaded"
                  width="600px"
                  height="375px" />
</template>

<script lang="ts">
import { Uploader } from "uploader";
import { UploadDropzone } from "@upload-io/vue-uploader";
import type { UploaderOptions, UploaderResult } from "uploader";

// One instance per app.
const uploader = Uploader({ apiKey: "free" });

// See "customization" below.
const options: UploaderOptions = {
  multi: true
};

export default {
  name: "App",
  components: {
    UploadDropzone
  },
  data() {
    return {
      uploader,
      options
    };
  },
  methods: {
    onFileUploaded: (files: UploaderResult[]) => {
      if (files.length === 0) {
        alert("No files selected.");
      } else {
        alert(files.map(f => f.fileUrl).join("\n"));
      }
    }
  }
};
</script>