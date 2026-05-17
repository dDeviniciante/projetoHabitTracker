<template>
  <div class="min-h-screen bg-zinc-950 text-white">
    <Sidebar :open="sidebarOpen" @toggle="sidebarOpen = !sidebarOpen" />

    <button
      v-if="!sidebarOpen"
      @click="sidebarOpen = true"
      class="fixed left-4 top-4 z-50 rounded-2xl border border-zinc-800 bg-zinc-950 p-3 text-xl text-white shadow-lg hover:bg-zinc-900 transition"
      aria-label="Abrir sidebar"
    >
      ☰
    </button>

    <div :class="[
      'min-h-screen transition-all duration-300',
      sidebarOpen ? 'lg:pl-[288px]' : 'lg:pl-0',
    ]">
      <div class="p-6 lg:p-8">
        <div class="max-w-7xl mx-auto space-y-8">
          <div class="flex flex-col gap-6 lg:flex-row lg:items-center lg:justify-between">
            <div>
              <h1 class="text-4xl font-bold tracking-tight">Habit Tracker</h1>
              <p class="text-zinc-400 mt-2">
                Organize hábitos, acompanhe consistência e visualize progresso.
              </p>
            </div>
            <button @click="showCreateModal = true" class="bg-white text-black px-5 py-3 rounded-2xl font-medium hover:scale-105 transition">
              + Novo hábito
            </button>
          </div>

          <div class="grid grid-cols-1 xl:grid-cols-[0.95fr_1.05fr] gap-8">
            <div class="space-y-6">
              <HabitList :habits="habits" />
              <HabitCalendar :habits="habits" />
            </div>

            <div class="space-y-6">
              <StatsPanel />
              <Heatmap />
            </div>
          </div>
        </div>
      </div>
    </div>

    <transition name="fade">
      <div v-if="showCreateModal" class="fixed inset-0 z-50 flex items-center justify-center">
        <div class="absolute inset-0 bg-black/60" @click="showCreateModal = false"></div>

        <div class="relative w-full max-w-3xl max-h-[90vh] overflow-auto rounded-3xl bg-zinc-900 border border-zinc-800 p-6 m-4">
          <button @click="showCreateModal = false" class="absolute right-4 top-4 rounded-full bg-zinc-800 p-2">
            ✕
          </button>
          <HabitForm :weekdays="weekdays" :metricTypes="metricTypes" />
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import HabitList from './components/HabitList.vue'
import HabitCalendar from './components/HabitCalendar.vue'
import HabitForm from './components/HabitForm.vue'
import StatsPanel from './components/StatsPanel.vue'
import Heatmap from './components/Heatmap.vue'
import Sidebar from './components/Sidebar.vue'

const sidebarOpen = ref(true)
const showCreateModal = ref(false)

onMounted(() => {
  const onKey = (e) => {
    if (e.key === 'Escape') showCreateModal.value = false
  }
  window.addEventListener('keydown', onKey)
})

const habits = [
  {
    emoji: '📘',
    name: 'Estudar Matemática',
    streak: 12,
    progress: [true, true, true, false, true, true, false],
  },
  {
    emoji: '💻',
    name: 'Programação',
    streak: 8,
    progress: [true, false, true, true, true, false, false],
  },
  {
    emoji: '📚',
    name: 'Leitura',
    streak: 21,
    progress: [true, true, true, true, true, true, true],
  },
  {
    emoji: '🏋️',
    name: 'Treino',
    streak: 5,
    progress: [false, true, true, false, true, false, true],
  },
]

const weekdays = ['SEG', 'TER', 'QUA', 'QUI', 'SEX', 'SAB', 'DOM']

const metricTypes = [
  '✔ Apenas concluir',
  '⏱ Tempo',
  '📄 Páginas',
  '📏 Distância',
  '🔁 Quantidade',
  '🏋️ Repetições',
]
</script>
