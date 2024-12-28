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
      <div class="flex flex-col lg:flex-row gap-4 px-4 pb-4">
        <div class="flex-1 grow relative">
          <canvas
            id="bio-canvas"
            style="background-color:yellow"
            @click="$router.push('bio')"
            @mouseover="showAboutMe = true"
            @mouseleave="showAboutMe = false"
          ></canvas>
          <div
            class="text-abt-me absolute"
            v-show="showAboutMe"
            @click="$router.push('bio')"
            @mouseover="showAboutMe = true"
            @mouseleave="showAboutMe = false"
          >
            <h1 class="text-4xl">
              About Me
            </h1>
          </div>
        </div>
        <div class="flex-1 grow">
          <canvas id="project-canvas" style="background-color:green"></canvas>
        </div>
        <div class="flex-1 grow">
          <canvas id="blog-canvas" style="background-color:aqua"></canvas>
        </div>
      </div>
    </section>
  </div>
</template>
<script setup>
  import { onMounted } from 'vue'
  import Types from '../constants/types'

  definePageMeta({
    layout: false,
  })

  const showAboutMe = ref(false)
  const bioSprites = []
  const projectSprites = []
  const blogSprites = []
  const bunnyWidth = 240
  const bunnyHeight = 320

  onMounted(() => {
    const bioCanvas = document.getElementById('bio-canvas')
    const projectCanvas = document.getElementById('project-canvas')
    const blogCanvas = document.getElementById('blog-canvas')
    resizeCanvas([bioCanvas, projectCanvas, blogCanvas])
    window.onresize = () => {
      resizeCanvas([bioCanvas, projectCanvas, blogCanvas])
    }
    const tilesheet = loadTilesheet('work_bunnies.png', () => {
      [ ...Array(12) ].forEach((_, i) => {
        bioSprites.push({
          img: tilesheet,
          sourceX: (i % 4) * bunnyWidth + (i % 4) * 1,
          sourceY: Math.floor(i/4) * bunnyHeight + Math.floor(i/4) * 1,
          sourceWidth: bunnyWidth,
          sourceHeight: bunnyHeight,
          type: Types.IMAGE
        })
      });
      [ ...Array(12) ].forEach((_, i) => {
        projectSprites.push({
          img: tilesheet,
          sourceX: (i % 4) * bunnyWidth + (i % 4) * 1,
          sourceY: Math.floor(i/4) * bunnyHeight + Math.floor(i/4) * 1,
          sourceWidth: bunnyWidth,
          sourceHeight: bunnyHeight,
          type: Types.IMAGE
        })
      });
      [ ...Array(12) ].forEach((_, i) => {
        blogSprites.push({
          img: tilesheet,
          sourceX: (i % 4) * bunnyHeight + (i % 4) * 1,
          sourceY: Math.floor(i/4) * bunnyWidth + Math.floor(i/4) * 1,
          sourceWidth: bunnyWidth,
          sourceHeight: bunnyHeight,
          type: Types.IMAGE
        })
      });
      animate(bioCanvas, bioSprites)
    })
  })

  const resizeCanvas = (canvases) => {
    canvases.forEach((canvas) => {
      canvas.width = canvas.offsetWidth
      const gap = 30
      const containerWidth = (canvas.offsetWidth)
      const finalBWidth = (containerWidth - 3 * 15)/4
      const finalBHeight = finalBWidth/bunnyWidth * bunnyHeight
      canvas.height = finalBHeight * 3 + 15 * 2
    })
  }

  const loadTilesheet = (filename, loadHandler) => {
    const tilesheet = new Image();
    tilesheet.addEventListener("load", loadHandler, false);
    tilesheet.src = filename;
    return tilesheet;
  }

  const animate = (canvas, sprites) =>{
    render(canvas, sprites)
    requestAnimationFrame(() => animate(canvas, sprites))
  }

  const render = (canvas, sprites) => {
    const ctx = canvas.getContext("2d");
    ctx.clearRect(0, 0, canvas.offsetWidth, canvas.height);
    const containerWidth = (canvas.offsetWidth)
    const finalBWidth = (containerWidth - 3 * 15)/4

    sprites.forEach((sprite, i) => {
      sprite.scale = finalBWidth/bunnyWidth
      sprite.x = (i % 4) * (bunnyWidth * sprite.scale) + i % 4 * 15
      sprite.y = Math.floor(i/4) * (bunnyHeight * sprite.scale) + Math.floor(i/4) * 15
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