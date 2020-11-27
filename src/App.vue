<template>
  <div id="app">
    <button @click="scanned = ''">reset</button>
    <div>Value: {{ scanned }}</div>
    <vue-qr-reader
      ref="qr"
      v-on:code-scanned="codeScanned"
      :stop-on-scanned="stopped"
      :use-back-camera="true"
      :draw-on-found="true"
      line-color="#00FF00"
      :line-width="20"
      :video-height="480"
      :video-width="640"
      :responsive="true"
      v-if="!scanned"
    >
    </vue-qr-reader>
  </div>
</template>

<script>
import VueQrReader from "vue-qr-reader/dist/lib/vue-qr-reader.umd.js";

export default {
  name: "App",

  components: {
    VueQrReader,
  },

  data: function() {
    return {
      scanned: "",
      stopped: true,
    };
  },
  methods: {
    codeScanned(event) {
      console.log(event);
      this.scanned = event;
    },
  },
};
</script>
