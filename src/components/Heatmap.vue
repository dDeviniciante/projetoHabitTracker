<template>
  <div class="bg-zinc-900 border border-zinc-800 rounded-3xl p-6">
    <h2 class="text-xl font-semibold mb-4">Heatmap</h2>
    <div class="grid grid-cols-7 gap-2">
      <div
        v-for="i in 35"
        :key="`heat-${i}`"
        :class="[
          'aspect-square rounded-md',
          i % 4 === 0 ? 'bg-green-500' : i % 3 === 0 ? 'bg-green-800' : 'bg-zinc-800',
        ]"
      ></div>
    </div>
  </div>
</template>
