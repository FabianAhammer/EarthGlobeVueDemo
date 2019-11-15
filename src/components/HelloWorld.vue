<template>
  <div class="bg">
    <vgl-renderer class="maxed" antialias :alpha="true">
      <vgl-scene>
        <vgl-sphere-geometry :width-segments="30" :height-segments="30"></vgl-sphere-geometry>
        <vgl-texture :src="require('../assets/earth.jpg')" center="0 0" name="texture"></vgl-texture>
        <vgl-mesh-standard-material map="texture"></vgl-mesh-standard-material>
        <vgl-mesh></vgl-mesh>
        <vgl-ambient-light></vgl-ambient-light>
        <vgl-directional-light position="90 `${y%1}` 42"></vgl-directional-light>
      </vgl-scene>
      <vgl-perspective-camera :orbit-position="`${x} ${y} ${z}`"></vgl-perspective-camera>
    </vgl-renderer>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      location: 0,
      x: 4,
      y: 1,
      z: 0
    };
  },
  methods: {
    rotate() {
      if (this.z > -10) this.z -= 0.001;
      else this.z = 0;
    }
  },
  mounted() {
    setInterval(this.rotate, 45);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.maxed {
  height: 100vh;
}
::v-deep iframe {
  display: none;
}
.bg {
  background-image: url("../assets/heaven.jpg");
  background-size: cover;
}
</style>
