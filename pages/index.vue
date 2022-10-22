<template>
  <div style="display: flex; flex-direction: column; height: 100%">
    <v-container>
      <div class="d-flex justify-center vidoe-view">
        <!-- @loadedmetadata="logDuration" -->
        <video @onplaying="test2" id="my-vid" ref="vid" @timeupdate="test">
          <source
            type="video/mp4"
            src="https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm"
          />
        </video>
      </div>
    </v-container>
    <div @click="startVid()" class="text-center pb-2">start</div>
    <div class="timeline-col" style="width: 100%; height: 100%">
      <Timeline @currentTime="(v) => changeCurrent(v)" :length="length" />
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      length: 0,
      run: false,
      vid: {},
    };
  },
  methods: {
    startVid() {
      console.log(this.vid.target);
      this.vid.target.play();
    },
    test(params) {
      console.log(params.target);
      console.log(params.target.currentTime);
      console.log(params.target.duration);
    },
    test2(params) {
      console.log("Test 2");
      console.log(params.target.currentTime);
      console.log(params.target.duration);
    },
    //  logDuration() {
    //   console.log('duration', this.$refs.videoPlayer.duration)
    // },
    changeCurrent(sec) {
      this.vid.target.currentTime = parseInt(sec);
    },
  },
  mounted() {
    this.$refs.vid.addEventListener(
      "loadeddata",
      (e) => {
        console.log("in");
        this.vid = e;
        this.length = e.target.duration;
      },
      false
    );
  },
};
</script>
<style >
.vidoe-view {
  min-height: 60vh;
  max-height: 65vh;
}
</style>
