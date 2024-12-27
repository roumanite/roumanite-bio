<template>
  <div>
    <section class="dark:bg-gray-900 test2">
      <div id="header1" class="flex py-8 px-4 mx-auto w-fit text-center lg:py-16">
        <img class="rounded-full w-36 h-36" src="/assets/avatar.png" alt="Extra large avatar">
        <div class="">
          <h1 class="mb-4 text-4xl font-extrabold tracking-tight leading-none text-gray-900 md:text-5xl lg:text-6xl dark:text-white">
            Hello World!
          </h1>
          <p class="text-lg font-normal text-gray-500 lg:text-xl px-16 dark:text-gray-400">
            You're looking at Grace Ariel's personal website
          </p>
          <p class="mb-8 text-lg font-normal text-gray-500 lg:text-xl px-16 dark:text-gray-400">
            To explore, hover over the bunnies to start!
          </p>
        </div>
      </div>
      <canvas style="background-color:yellow"></canvas>
    </section>
  </div>
</template>
<script setup>
  import { onMounted } from 'vue'
  import Types from '../constants/types'

  definePageMeta({
    layout: false,
  })

  const sprites = []
  const bunnyWidth = 179
  const bunnyHeight = 244

  onMounted(() => {
    const canvas = document.querySelector("canvas")
    resizeCanvas(canvas)
    window.onresize = () => resizeCanvas(canvas)
    const tilesheet = loadTilesheet('work_bunnies.png', () => {
      [ ...Array(12) ].forEach((_, i) => {
        sprites.push({
          img: tilesheet,
          sourceX: (i % 4) * 179 + (i % 4) * 1,
          sourceY: Math.floor(i/4) * 244 + Math.floor(i/4) * 1,
          sourceWidth: bunnyWidth,
          sourceHeight: bunnyHeight,
          type: Types.IMAGE
        })
      });
      [ ...Array(12) ].forEach((_, i) => {
        sprites.push({
          img: tilesheet,
          sourceX: (i % 4) * 179 + (i % 4) * 1,
          sourceY: Math.floor(i/4) * 244 + Math.floor(i/4) * 1,
          sourceWidth: bunnyWidth,
          sourceHeight: bunnyHeight,
          type: Types.IMAGE
        })
      });
      [ ...Array(12) ].forEach((_, i) => {
        sprites.push({
          img: tilesheet,
          sourceX: (i % 4) * 179 + (i % 4) * 1,
          sourceY: Math.floor(i/4) * 244 + Math.floor(i/4) * 1,
          sourceWidth: bunnyWidth,
          sourceHeight: bunnyHeight,
          type: Types.IMAGE
        })
      });
      update(canvas)
    })
  })

  const resizeCanvas = (canvas) => {
    canvas.width = window.innerWidth
    const header = document.getElementById("header1")
    canvas.height = window.innerHeight - header.clientHeight
  }

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
    const gap = 30
    const containerWidth = (canvas.width - gap * 4)/3
    const finalBWidth = (containerWidth - 3 * 15)/4

    sprites.forEach((sprite, i) => {
      sprite.scale = finalBWidth/bunnyWidth
      let col = 1
      let row = 1
      let n = i
      if (i > 11 && i < 24) {
        col = 2
        n -= 12
      } else if (i > 23) {
        col = 3
        n -= 24
      }
      sprite.x = (n % 4) * (bunnyWidth * sprite.scale) + gap * col + n % 4 * 15 + containerWidth * (col - 1)
      sprite.y = Math.floor(n/4) * (bunnyHeight * sprite.scale) + gap + Math.floor(n/4) * 15
      switch (sprite.type) {
        case Types.RECTANGLE:
          ctx.fillStyle = 'rgba(10, 30, 100, 0.5)'
          ctx.fillRect(sprite.x, sprite.y, previewWidth, previewHeight)
          break
        case Types.IMAGE:
          ctx.drawImage(
            sprite.img,
            sprite.sourceX, sprite.sourceY,
            sprite.sourceWidth, sprite.sourceHeight,
            sprite.x,
            sprite.y,
            sprite.sourceWidth * sprite.scale, sprite.sourceHeight * sprite.scale,
          )
          break
        default:
          break
      }
    })
  }
</script>