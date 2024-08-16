<template>
  <h1 class="mb-4 text-4xl font-extrabold tracking-tight leading-none text-gray-900 md:text-5xl lg:text-6xl dark:text-white">
    Projects
  </h1>
  <canvas></canvas>
</template>
<script setup>
  import { onMounted } from 'vue'
  import Types from '../constants/types'

  const sprites = []
  onMounted(() => {
    const canvas = document.querySelector("canvas")
    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
    const tilesheet = loadTilesheet('tilesheet.png', () => {
      sprites.push({
        img: tilesheet,
        x: canvas.width/2 - 285/2,
        y: 0,
        scale: 1,
        sourceX: 0,
        sourceY: 0,
        sourceWidth: 285,
        sourceHeight: 301,
        type: Types.IMAGE
      })
    })
    update(canvas)
  })
  const loadTilesheet = (filename, loadHandler) => {
    const tilesheet = new Image();
    tilesheet.addEventListener("load", loadHandler, false);
    tilesheet.src = filename;
    return tilesheet;
  }
  const update = (canvas) =>{
    requestAnimationFrame(() => update(canvas))
    render(canvas)
  }
  const render = (canvas) => {
    const ctx = canvas.getContext("2d");
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    sprites.forEach(sprite => {
      if (sprite.type === Types.IMAGE) {
        ctx.drawImage(
          sprite.img,
          sprite.sourceX, sprite.sourceY,
          sprite.sourceWidth, sprite.sourceHeight,
          sprite.x,
          sprite.y,
          sprite.sourceWidth * sprite.scale, sprite.sourceHeight * sprite.scale,
        )
      }
    })
  }
</script>
