<script setup lang="ts">
defineProps<{ video: string }>();
</script>

<template>
  <div class="slidev-layout video">
    <div class="my-auto mx-auto w-full">
      <div class="w-full h-[440px]">
        <slot />
        <iframe v-if="video.startsWith('http')" :src="`${video}?rel=0`" class="w-full h-[420px]" frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen>
        </iframe>
        <SlidevVideo v-else class="w-full min-h-[420px]" controls>
          <source :src="video" type="video/mp4" />
          <p>
            你的浏览器不支持播放该视频，请点击
            <a :href="video">此处</a>
            下载。
          </p>
        </SlidevVideo>
      </div>
    </div>
  </div>
</template>
