<template>
  <div id="app">
    <div class="video-container">
      <div class="overlay">
        <video
          class="video-container__background"
          poster="background-video.jpg"
          muted="true"
          autoplay="true"
          loop="true"
        >
          <source src="video-bg.mp4" type="video/mp4" />
        </video>
      </div>
      <div class="video-container__content">
        <Counter />
      </div>
    </div>
  </div>
</template>

<script>
import Counter from "./components/Counter";
export default {
  name: "app",
  components: {
    Counter
  }
};
</script>

<style>
html,
body,
div,
span {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  vertical-align: baseline;
}
body {
  font-family: "Lato", sans-serif;
}

.video-container {
  position: relative;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
}

.video-container__background {
  z-index: -1;
  position: absolute;
  width: auto;
  height: auto;
  min-width: 100%;
  min-height: 100%;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}

.video-container .overlay {
  position: absolute;
  width: auto;
  height: auto;
  min-width: 100%;
  min-height: 100%;
  background-color: rgba(0, 0, 0, 0.6);
}
.video-container__content {
  color: white;
  z-index: 2;
}
</style>
