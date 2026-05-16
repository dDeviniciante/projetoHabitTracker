<template>
  <div class="bg-zinc-900 border border-zinc-800 rounded-3xl p-6">
    <div class="flex items-center justify-between mb-6 gap-4">
      <div>
        <p class="text-zinc-500 text-sm">Desempenho</p>
        <h2 class="text-2xl font-semibold mt-1">Estatísticas</h2>
      </div>
      <button class="bg-zinc-950 border border-zinc-800 px-4 py-2 rounded-xl text-sm hover:bg-zinc-800 transition whitespace-nowrap">Ver detalhes</button>
    </div>

    <div class="space-y-5">
      <div>
        <div class="flex justify-between text-sm mb-2 text-zinc-400">
          <span>Consistência semanal</span>
          <span>84%</span>
        </div>

        <div class="flex items-end gap-2 h-28">
          <div
            v-for="height in [45, 70, 55, 90, 60, 100, 80]"
            :key="height"
            class="flex-1 bg-white rounded-t-2xl opacity-90"
            :style="{ height: `${height}%` }"
          ></div>
        </div>
      </div>

      <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
        <div class="bg-zinc-950 border border-zinc-800 rounded-2xl p-4">
          <p class="text-zinc-500 text-sm">Melhor streak</p>
          <h3 class="text-3xl font-bold mt-2">21</h3>
        </div>
        <div class="bg-zinc-950 border border-zinc-800 rounded-2xl p-4">
          <p class="text-zinc-500 text-sm">Dias ativos</p>
          <h3 class="text-3xl font-bold mt-2">142</h3>
        </div>
      </div>
    </div>
  </div>
</template>
