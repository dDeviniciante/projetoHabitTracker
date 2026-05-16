<template>
  <div class="min-h-screen bg-zinc-950 text-white p-6 lg:p-8">
    <div class="max-w-7xl mx-auto space-y-8">
      <div class="flex flex-col gap-6 lg:flex-row lg:items-center lg:justify-between">
        <div>
          <h1 class="text-4xl font-bold tracking-tight">Habit Tracker</h1>
          <p class="text-zinc-400 mt-2">
            Organize hábitos, acompanhe consistência e visualize progresso.
          </p>
        </div>
        <button class="bg-white text-black px-5 py-3 rounded-2xl font-medium hover:scale-105 transition">
          + Novo hábito
        </button>
      </div>

      <div class="grid grid-cols-1 xl:grid-cols-[0.95fr_1.05fr] gap-8">
        <div class="space-y-6">
          <HabitList :habits="habits" />
          <HabitCalendar :habits="habits" />
        </div>

        <div class="space-y-6">
          <HabitForm :weekdays="weekdays" :metricTypes="metricTypes" />
          <StatsPanel />
          <Heatmap />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import HabitList from './components/HabitList.vue'
import HabitCalendar from './components/HabitCalendar.vue'
import HabitForm from './components/HabitForm.vue'
import StatsPanel from './components/StatsPanel.vue'
import Heatmap from './components/Heatmap.vue'

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
