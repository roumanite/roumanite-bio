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
            To start exploring, hover over the bunnies!
          </p>
        </div>
      </div>
      <div class="flex flex-col lg:flex-row gap-4 px-4 pb-4">
        <div class="flex-1 grow relative">
          <canvas
            id="bio-canvas"
            style="background-color:yellow"
            @click="$router.push('bio')"
            @mouseover="toggleShowAboutMe(true)"
            @mouseleave="toggleShowAboutMe(false)"
          ></canvas>
          <div
            class="text-abt-me absolute"
            v-show="showAboutMe"
            @click="$router.push('bio')"
            @mouseover="toggleShowAboutMe(true)"
            @mouseleave="toggleShowAboutMe(false)"
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
  let oldCanvasWidth = null

  onMounted(() => {
    const bioCanvas = document.getElementById('bio-canvas')
    const projectCanvas = document.getElementById('project-canvas')
    const blogCanvas = document.getElementById('blog-canvas')
    resizeCanvas([bioCanvas, projectCanvas, blogCanvas])
    oldCanvasWidth = bioCanvas.offsetWidth
    window.onresize = () => {
      resizeCanvas([bioCanvas, projectCanvas, blogCanvas])
      render(bioCanvas, bioSprites)
      render(projectCanvas, projectSprites)
      render(blogCanvas, blogSprites)
      oldCanvasWidth = bioCanvas.offsetWidth
    }
    const tilesheet = loadTilesheet('work_bunnies.png', () => {
      [ ...Array(12) ].forEach((_, i) => {
        bioSprites.push({
          img: tilesheet,
          sourceX: (i % 4) * bunnyWidth + (i % 4) * 3,
          sourceY: Math.floor(i/4) * bunnyHeight + Math.floor(i/4) * 3,
          speedX: 0,
          speedY: 0,
          sourceWidth: bunnyWidth,
          sourceHeight: bunnyHeight,
          type: Types.IMAGE
        })
      });
      render(bioCanvas, bioSprites)
    })
    const tilesheet2 = loadTilesheet('project_bunnies.png', () => {
      [ ...Array(12) ].forEach((_, i) => {
        projectSprites.push({
          img: tilesheet2,
          sourceX: (i % 4) * bunnyWidth + (i % 4) * 3,
          sourceY: Math.floor(i/4) * bunnyHeight + Math.floor(i/4) * 3,
          speedX: 0,
          speedY: 0,
          sourceWidth: bunnyWidth,
          sourceHeight: bunnyHeight,
          type: Types.IMAGE
        })
      });
      render(projectCanvas, projectSprites)
    })
    const tilesheet3 = loadTilesheet('author_bunnies.png', () => {
      [ ...Array(12) ].forEach((_, i) => {
        blogSprites.push({
          img: tilesheet3,
          sourceX: (i % 4) * bunnyWidth + (i % 4) * 3,
          sourceY: Math.floor(i/4) * bunnyHeight + Math.floor(i/4) * 3,
          speedX: 0,
          speedY: 0,
          sourceWidth: bunnyWidth,
          sourceHeight: bunnyHeight,
          type: Types.IMAGE
        })
      });
      render(blogCanvas, blogSprites)
    })
  })

  const toggleShowAboutMe = (val) => {
    showAboutMe.value = val
    if (showAboutMe.value) {
      const bioCanvas = document.getElementById('bio-canvas')
      bioSprites.forEach((sprite) => sprite.speedX = 1)
      animate(bioCanvas, bioSprites, showAboutMe)
    } else {
      bioSprites.forEach((sprite) => sprite.speedX = 0)
    }
  }

  const resizeCanvas = (canvases) => {
    canvases.forEach((canvas) => {
      canvas.width = canvas.offsetWidth
      const resizedHeight = getBunnyHeight(canvas.width, 4, 15)
      canvas.height = resizedHeight * 3 + 15 * 2
    })
  }

  const loadTilesheet = (filename, loadHandler) => {
    const tilesheet = new Image();
    tilesheet.addEventListener("load", loadHandler, false);
    tilesheet.src = filename;
    return tilesheet;
  }

  const animate = (canvas, sprites, stateRef) => {
    render(canvas, sprites)
    if (stateRef.value) {
      requestAnimationFrame(() => animate(canvas, sprites, stateRef))
    }
  }

  const render = (canvas, sprites) => {
    update(canvas, sprites)
    draw(canvas, sprites)
  }

  const update = (canvas, sprites) => {
    sprites.forEach((sprite, i) => {
      sprite.scale = getBunnyWidth(canvas.width, 4, 15)/bunnyWidth
      if (sprite.x === undefined) {
        sprite.x = getOriginX(i, bunnyWidth, sprite.scale, 4, 15)
        sprite.y = getOriginY(i, bunnyHeight, sprite.scale, 4, 15)
      } else if (canvas.offsetWidth !== oldCanvasWidth) {
        const oldX = sprite.x
        const oldScale = getBunnyWidth(oldCanvasWidth, 4, 15)/bunnyWidth
        const oldOriX = getOriginX(i, bunnyWidth, oldScale, 4, 15)
        const oriX = getOriginX(i, bunnyWidth, sprite.scale, 4, 15)
        const travel = getDistance(oldCanvasWidth, 15, oldX, oldOriX)
        const newTravel = scaleDistance(travel, oldCanvasWidth, canvas.width)
        sprite.x = (oriX + newTravel) % (canvas.width + 15)
        sprite.y = getOriginY(i, bunnyHeight, sprite.scale, 4, 15)
      }
      sprite.x += sprite.speedX
      sprite.y += sprite.speedY
      if (sprite.x > canvas.width) {
        sprite.x = sprite.x - bunnyWidth * sprite.scale * 4 - 15 * 4
      }
    })
  }

  const getBunnyWidth = (canvasWidth, cols, gap) => (canvasWidth - (cols-1) * gap)/cols

  const getBunnyHeight = (canvasWidth, cols, gap) => {
    const width = getBunnyWidth(canvasWidth, cols, gap)
    return width/bunnyWidth * bunnyHeight
  }

  const getDistance = (
    canvasLength,
    gap,
    coordinate,
    originCoordinate
  ) => {
    let travel = coordinate - originCoordinate
    if (travel < 0) {
      travel = travel + canvasLength + gap
    }
    return travel
  }

  const scaleDistance = (oldDistance, oldCanvasLength, newCanvasLength) => {
    return Math.round(oldDistance/oldCanvasLength * newCanvasLength)
  } 

  const draw = (canvas, sprites) => {
    const ctx = canvas.getContext("2d");
    ctx.clearRect(0, 0, canvas.offsetWidth, canvas.height);

    sprites.forEach((sprite, _) => {
      switch (sprite.type) {
        case Types.RECTANGLE:
          ctx.fillStyle = 'rgba(10, 30, 100, 0.5)'
          ctx.fillRect(sprite.x, sprite.y, previewWidth, previewHeight)
          break
        case Types.IMAGE:
          const scaledWidth = sprite.sourceWidth * sprite.scale
          const scaledHeight = sprite.sourceHeight * sprite.scale
          ctx.drawImage(
            sprite.img,
            sprite.sourceX, sprite.sourceY,
            sprite.sourceWidth, sprite.sourceHeight,
            sprite.x,
            sprite.y,
            scaledWidth, scaledHeight,
          )
          if (sprite.x + scaledWidth > canvas.width) {
            const overflow = (sprite.x + scaledWidth) - canvas.width;
            ctx.drawImage(
              sprite.img,
              sprite.sourceX, sprite.sourceY,
              sprite.sourceWidth, sprite.sourceHeight,
              -scaledWidth + overflow - 15, sprite.y,
              scaledWidth, scaledHeight
            );
          }
          break
        default:
          break
      }
    })
  }

  const getOriginX = (i, width, scale, cols, gap) => (i % cols) * width * scale + i % cols * gap
  const getOriginY = (i, height, scale, cols, gap) => Math.floor(i/cols) * height * scale + Math.floor(i/cols) * gap
</script>