<template>
  <div>
    <a-alert message="图片依次加载" type="info" />
    <div class="container">
      <img v-for="src in imgs" :src="src" class="img" />
    </div>
  </div>
</template>

<script setup lang="ts">
const imgs = [
  'https://appimg.dbankcdn.com/application/icon144/ef3e86d75d6d44e78486cf4696ba4817.png',
  'https://appimg.dbankcdn.com/application/icon144/91771a4c7b38427db0924bcbcc601c0d.png',
  'https://appimg.dbankcdn.com/application/icon144/359077f2e88147bb81ce5cc8b420230c.png',
  'https://appimg.dbankcdn.com/application/icon144/154b3bc2c59a4a09b5dc8841b70eb47b.png',
  'https://appimg.dbankcdn.com/application/icon144/b1148afa90704b59b9cff9baa7749bda.png',
  'https://appimg.dbankcdn.com/application/icon144/b6fea3f0d91b450992466c8283aa17b3_1.png',
  'https://appimg.dbankcdn.com/application/icon144/af253cd113864ae5ba9093534e71066e.png',
  'https://appimg.dbankcdn.com/application/icon144/f81a5f8e63a84e9b87332c2e00ad867d.png',
  'https://appimg.dbankcdn.com/application/icon144/6c5a95b128c540e3be1792ecb226bf44.png',
  'https://appimg.dbankcdn.com/application/icon144/24c0605971da428b8681a9b388644eea.png',
];

// 实现一个方法，加载指定url的图片，要求返回一个promise
function loadImg(url: string): Promise<void> {
  return new Promise((resolve, reject) => {
    const imageNode = new Image();
    imageNode.src = url;
    imageNode.onload = () => resolve();
    imageNode.onerror = reject;
  });
}

function delay(delayTime: number): Promise<void> {}

// 有n张图片url，要求实现一个方法，可以依次加载这些图片，第一个加载完成后才加载第二个
async function loadImgs(urls: string[]): Promise<void> {}
loadImgs(imgs);
// 在图片加载时，设定一个超时时间3秒，比如某一张图片如果加载超过3秒，则不再等待，直接去加载下一张图片。该如何实现
async function loadImgWithTimeout(urls: string[], delayTime) {}
</script>

<style scoped>
.container {
  margin-top: 10px;
}
.img {
  width: 100px;
  margin: 0 10px 10px 0;
}
</style>
