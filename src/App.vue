
<template>
   <button @click="loadImage">Analyze Image</button>
   <canvas ref="myCanvas" width="600" height="400"></canvas>
  
</template>

<style>
@import './assets/base.css';

</style>

<script setup>
import '@tensorflow/tfjs-backend-cpu';
import '@tensorflow/tfjs-backend-webgl';
import * as cocoSsd from '@tensorflow-models/coco-ssd';
import imgSrc from './assets/test.jpg';
import {ref} from 'vue';
const img = ref(null);
const myCanvas = ref(null);
async function loadImage() {
  const img = new Image();
  img.src = imgSrc;
  // Load the model.
  const model = await cocoSsd.load();

  // Classify the image.
  const predictions = await model.detect(img);

  console.log('Predictions: ');
  // console.log(predictions);
  drawImage(predictions, img);
}

function drawImage(predictions, image) {
  // const canvas = document.querySelector('#canvas');
  const context = myCanvas.value.getContext('2d');
  console.log(context);

  context.drawImage(image, 0, 0, myCanvas.value.width, myCanvas.value.height);
  context.font = '12px arial';

  predictions.forEach((prediction) => {
    console.log(prediction);
    context.beginPath();
    context.rect(...prediction.bbox);
    context.lineWidth = 1;
    context.strokeStyle = 'green';
    context.fillStyle = 'black';
    context.stroke();

    context.fillText(
      `${prediction.class} (${prediction.score.toFixed(3)})`,
      prediction.bbox[0],
      prediction.bbox[1],
    );
  });
}
</script>

