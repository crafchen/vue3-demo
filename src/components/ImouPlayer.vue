<script lang="ts" setup>
import { onMounted } from "vue";

interface IPlayer {
  play: Function;
  stop: Function;
  pause: Function;
  capture: Function;
  startTalk: Function;
  stopTalk: Function;
  volume: Function;
  fullScreen: Function;
  exitFullScreen: Function;
  startRecord: Function;
  stopRecord: Function;
  destroy: Function;
}

let player: IPlayer;

const play = () => {
  player.play();
};
const pause = () => {
  player.pause();
};
const stop = () => {
  player.stop();
};
const capture = () => {
  player.capture();
};
const startTalk = () => {
  player.startTalk();
};
const stopTalk = () => {
  player.stopTalk();
};
const volume = (value) => {
  player.volume(value);
};
const fullScreen = () => {
  player.fullScreen();
};
const exitFullScreen = () => {
  player.exitFullScreen();
};
const startRecord = () => {
  player.startRecord();
};
const stopRecord = () => {
  player.stopRecord();
};

const destroy = () => {
  player.destroy();
  player = null!;
};

const init = () => {
  if (player) {
    destroy();
  }
  player = new imouPlayer({
    id: "imou-player",
    width: 1200,
    height: 700,
    deviceId: "A2FC0AMPSFFA4424",
    channelId: "0",
    token: "*******************",
    type: 1,
    streamId: 0,
    recordType: "cloud",
    muted: false,
    handleError: (err) => {
      console.error("handleError", err);
    },
  });
  window.player = player;
};

onMounted(() => {
  // init();
});
</script>

<template>
  <div class="imou-player">
    <div
      id="imou-player"
      style="width: 1200px; height: 700px; background-color: #000"
    ></div>
    <div>
      <button @click="init">Init imouPlayer</button>
      <button @click="play">Play</button>
      <button @click="pause">Pause</button>
      <button @click="stop">Stop</button>
      <button @click="capture">Capture</button>
      <button @click="startTalk">Start Talk</button>
      <button @click="stopTalk">Stop Talk</button>
      <button @click="() => volume(1)">Open Volume</button>
      <button @click="() => volume(0)">Close Volume</button>
      <button @click="fullScreen">FullScreen</button>
      <button @click="exitFullScreen">Exit FullScreen</button>
      <button @click="startRecord">Start Screen Recording</button>
      <button @click="stopRecord">Stop Screen Recording</button>
    </div>
  </div>
</template>
