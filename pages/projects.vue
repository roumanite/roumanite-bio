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
  const bunnyWidth = 285
  const bunnyHeight = 301
  const previewWidth = 100
  const previewHeight = 100

  onMounted(() => {
    const canvas = document.querySelector("canvas")
    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
    const originX = canvas.width/2
    const originY = 0 + bunnyHeight/2
    const tilesheet = loadTilesheet('tilesheet.png', () => {
      sprites.unshift({
        img: tilesheet,
        x: canvas.width/2 - bunnyWidth/2,
        y: 0,
        scale: 1,
        sourceX: 0,
        sourceY: 0,
        sourceWidth: bunnyWidth,
        sourceHeight: bunnyHeight,
        type: Types.IMAGE
      })
      const previews = [{
        img: tilesheet,
        x: originX - previewWidth/2,
        y: originY - previewHeight/2,
        scale: 1,
        sourceX: 91,
        sourceY: 200,
        sourceWidth: previewWidth,
        sourceHeight: previewHeight,
        type: Types.IMAGE,
      }, {
        img: tilesheet,
        x: originX - previewWidth/2,
        y: originY - previewHeight/2,
        scale: 1,
        sourceX: 110,
        sourceY: 413,
        sourceWidth: previewWidth,
        sourceHeight: previewHeight,
        type: Types.IMAGE,
      }]
      previews.forEach((preview, previewNo) => {
        const destX = 50 + previewNo * 150
        const destY = bunnyHeight + 50 + Math.floor(1/10) * 150
        const midDestX = destX + previewWidth/2
        const midDestY = destY + previewHeight/2
        const [xCoords, yCoords] = getDistancedPoints(8, { x1: originX, y1: originY, x2: midDestX, y2: midDestY })
        xCoords.forEach((x, i) => {
          setTimeout(() => {
            preview.x = x - previewWidth/2
            preview.y = yCoords[i] - previewHeight/2
          }, 100 * i + previewNo * 800)
        })
      })
      sprites.push(...previews)
    })
    update(canvas)
  })
  const getDistancedPoints = (distance, coords) => {
    const diffX = coords.x1 - coords.x2
    const diffY = coords.y1 - coords.y2
    const intervalX = diffX / (distance + 1)
    const intervalY = diffY / (distance + 1)
    const xList = [coords.x1]
    const yList = [coords.y1]

    for (let i = distance; i >= 0; i--) {
      xList.push(coords.x2 + intervalX * i)
      yList.push(coords.y2 + intervalY * i)
    }

    xList.push(coords.x2)
    yList.push(coords.y2)

    return [xList, yList]
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
    sprites.forEach(sprite => {
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
