<template>
  <!-- <VideoEditingTimeline :config="config" /> -->
  <div
    style="overflow-x: scroll; height: 100%"
    class="d-flex overflow-scroll justify-space-between"
  >
    <div
      :style="sec % 5 != 0 ? 'width:1px !important' : ''"
      class="px-2"
      :key="sec"
      v-for="sec in Math.floor(length)"
    >
      <div>
        <span  @click="test(sec)" style="background-color: grey; width: 2px ; cursor: pointer">&nbsp;</span><br />
        <span
          style="cursor: pointer"
          @click="test(sec)"
          v-if="sec % 5 == 0 || sec == 1"
          >{{ sec }}</span
        >
        <!-- <span style="" class="test" @click="test(sec)" v-else>
        </span> -->
      </div>
    </div>
  </div>
</template>

<script>
// import VideoEditingTimeline from "video-editing-timeline-vue";
export default {
  props: ["length"],
  //   components: {
  //     VideoEditingTimeline,
  //   },
  data() {
    return {
      //   config: {
      //     canvasWidth: 1300,
      //     canvasHeight: 50,
      //     minimumScale: 10,
      //     minimumScaleTime: 1,
      //   },
    };
  },
  methods: {
    test(sec) {
      console.log(sec);
      this.$emit("currentTime", sec);
    },
  },
};
</script>
<style scoped>
.test::after {
  content: " | ";
  display: inline-block;
  padding-left: 22px;
  color: rgba(67, 46, 140, 0.5);
}
</style>