<template>
  <aside
    :class="[
      'fixed left-0 top-0 bottom-0 z-50 w-72 overflow-y-auto border-r border-zinc-800 bg-zinc-950 transition-transform duration-300 shadow-xl',
      open ? 'translate-x-0' : '-translate-x-full',
    ]"
  >
    <div class="flex items-center justify-between px-6 py-5 border-b border-zinc-800">
      <div>
        <p class="text-zinc-500 text-sm">Workspace</p>
        <h2 class="text-xl font-semibold">Rastreador</h2>
      </div>
      <button
        @click="$emit('toggle')"
        aria-label="Fechar sidebar"
        class="rounded-2xl bg-zinc-900 px-3 py-2 text-zinc-200 hover:bg-zinc-800 transition"
      >
        ✕
      </button>
    </div>

    <div class="px-6 py-4 space-y-4">
      <div class="space-y-3 rounded-3xl bg-zinc-900 p-4 border border-zinc-800">
        <button class="w-full flex items-center gap-3 rounded-2xl bg-white/10 px-4 py-3 text-left text-white hover:bg-white/10 transition">
          <span class="text-lg">🏠</span>
          <span>Home</span>
        </button>
        <button class="w-full flex items-center gap-3 rounded-2xl px-4 py-3 text-left text-zinc-300 hover:bg-white/5 transition">
          <span class="text-lg">💡</span>
          <span>Projetos</span>
        </button>
        <button class="w-full flex items-center gap-3 rounded-2xl px-4 py-3 text-left text-zinc-300 hover:bg-white/5 transition">
          <span class="text-lg">📊</span>
          <span>Desempenho</span>
        </button>
      </div>

      <div class="space-y-2">
        <p class="text-zinc-500 text-xs uppercase tracking-[0.2em]">Recents</p>
        <button class="w-full flex items-center gap-3 rounded-2xl px-4 py-3 text-left text-zinc-300 hover:bg-zinc-900 transition">
          <span class="text-lg">📘</span>
          <span>Rastreador de Hábitos</span>
        </button>
        <button class="w-full flex items-center gap-3 rounded-2xl px-4 py-3 text-left text-zinc-300 hover:bg-zinc-900 transition">
          <span class="text-lg">🏆</span>
          <span>My performances</span>
        </button>
        <button class="w-full flex items-center gap-3 rounded-2xl px-4 py-3 text-left text-zinc-300 hover:bg-zinc-900 transition">
          <span class="text-lg">📚</span>
          <span>Minha Biblioteca</span>
        </button>
      </div>

      <div class="rounded-3xl bg-zinc-900 border border-zinc-800 p-4 text-sm text-zinc-400">
        <p class="text-white font-semibold">Dica do dia</p>
        <p class="mt-2 leading-relaxed">
          Use o menu para alternar entre hábitos, metas e relatórios com rapidez.
        </p>
      </div>
    </div>
  </aside>
</template>

<script setup>
const props = defineProps({
  open: {
    type: Boolean,
    default: true,
  },
})
</script>
