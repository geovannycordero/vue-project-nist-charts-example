<template>
  <div class="p-6 my-10 mx-auto max-w-4xl">
    <h1 class="text-3xl font-bold mb-6">Perfil de la Compañía</h1>

    <Line
      id="multi-axis-line-chart"
      class="w-full h-96"
      :options="chartOptions2"
      :data="chartData2"
    />

    <Radar
      id="radar-chart"
      class="w-full h-96 mt-28"
      :options="chartOptions3"
      :data="chartData3"
    />

    <h2 class="text-2xl font-semibold mt-28">
      Indicadores de trabajo último trimestre
    </h2>
    <h3 class="text-xl font-medium mt-5 text-gray-600">
      Accionables para llegar a perfil recomendado
    </h3>
    <section class="mt-10">
      <h2 class="text-xl font-medium mb-4">Auditorías de Cumplimiento</h2>
      <ul class="list-disc list-inside text-gray-700 mb-4">
        <li class="flex items-center mb-2">
          <input type="checkbox" class="mr-2" />
          <span>Revisión de políticas de seguridad</span>
          <button
            class="ml-auto text-blue-500 bg-transparent px-4 py-2 rounded flex items-center hover:bg-blue-100"
          >
            Adjuntar
          </button>
        </li>
        <li class="flex items-center mb-2">
          <input type="checkbox" class="mr-2" />
          <span>Evaluación de cumplimiento normativo</span>
          <button
            class="ml-auto text-blue-500 bg-transparent px-4 py-2 rounded flex items-center hover:bg-blue-100"
          >
            Adjuntar
          </button>
        </li>
      </ul>
    </section>

    <section class="mt-10">
      <h2 class="text-xl font-medium mb-4">Gestión de Riesgos de Terceros</h2>
      <ul class="list-disc list-inside text-gray-700 mb-4">
        <li class="flex items-center mb-2">
          <input type="checkbox" class="mr-2" />
          <span>Evaluación de riesgos de proveedores</span>
          <button
            class="ml-auto text-blue-500 bg-transparent px-4 py-2 rounded flex items-center hover:bg-blue-100"
          >
            Adjuntar
          </button>
        </li>
        <li class="flex items-center mb-2">
          <input type="checkbox" class="mr-2" />
          <span>Monitoreo continuo de terceros</span>
          <button
            class="ml-auto text-blue-500 bg-transparent px-4 py-2 rounded flex items-center hover:bg-blue-100"
          >
            Adjuntar
          </button>
        </li>
      </ul>
    </section>

    <section class="mt-10">
      <h2 class="text-xl font-medium mb-4">Gestión de Vulnerabilidades</h2>
      <ul class="list-disc list-inside text-gray-700 mb-4">
        <li class="flex items-center mb-2">
          <input type="checkbox" class="mr-2" />
          <span>Evaluación de riesgos de proveedores</span>
          <button
            class="ml-auto text-blue-500 bg-transparent px-4 py-2 rounded flex items-center hover:bg-blue-100"
          >
            Adjuntar
          </button>
        </li>
        <li class="flex items-center mb-2">
          <input type="checkbox" class="mr-2" />
          <span>Monitoreo continuo de vulnerabilidades</span>
          <button
            class="ml-auto text-blue-500 bg-transparent px-4 py-2 rounded flex items-center hover:bg-blue-100"
          >
            Adjuntar
          </button>
        </li>
      </ul>
    </section>

    <section class="mt-10">
      <h2 class="text-xl font-medium mb-4">Pruebas de Penetración</h2>
      <ul class="list-disc list-inside text-gray-700 mb-4">
        <li class="flex items-center mb-2">
          <input type="checkbox" class="mr-2" />
          <span>Planificación de pruebas de penetración</span>
          <button
            class="ml-auto text-blue-500 bg-transparent px-4 py-2 rounded flex items-center hover:bg-blue-100"
          >
            Adjuntar
          </button>
        </li>
        <li class="flex items-center mb-2">
          <input type="checkbox" class="mr-2" />
          <span>Ejecutar pruebas de penetración</span>
          <button
            class="ml-auto text-blue-500 bg-transparent px-4 py-2 rounded flex items-center hover:bg-blue-100"
          >
            Adjuntar
          </button>
        </li>
      </ul>
    </section>

    <Bar
      id="mi-grafico-id"
      class="w-full h-96 mt-10 mb-28"
      :options="chartOptions"
      :data="chartData"
    />

    <InformationModal
      :isOpen="isOpen"
      :profile="profile"
      :data="profileData"
      :setIsOpen="setIsOpen"
    />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { Line, Radar, Bar } from 'vue-chartjs'
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
  LineElement,
  PointElement,
  RadialLinearScale,
  Filler,
} from 'chart.js'

import InformationModal from '@/components/modals/InformationModal.vue'

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
  LineElement,
  PointElement,
  RadialLinearScale,
  Filler,
)

const handleClick2 = (
  _event: MouseEvent,
  elements: Array<{ datasetIndex: number; index: number }>,
) => {
  if (elements.length > 0) {
    const element = elements[0]
    const datasetIndex = element.datasetIndex
    const index = element.index
    const dataset = chartData2.value.datasets[datasetIndex]
    const data = dataset.data[index]

    profile.value = dataset.label
    profileData.value = data.toString()
    setIsOpen(true)
  }
}

const handleClick3 = (
  _event: MouseEvent,
  elements: Array<{ datasetIndex: number; index: number }>,
) => {
  if (elements.length > 0) {
    const element = elements[0]
    const datasetIndex = element.datasetIndex
    const index = element.index
    const dataset = chartData3.value.datasets[datasetIndex]
    const data = dataset.data[index]

    profile.value = dataset.label
    profileData.value = data.toString()
    setIsOpen(true)
  }
}

const chartData2 = ref({
  labels: [
    'Enero',
    'Febrero',
    'Marzo',
    'Abril',
    'Mayo',
    'Junio',
    'Julio',
    'Agosto',
    'Septiembre',
    'Octubre',
    'Noviembre',
    'Diciembre',
  ],
  datasets: [
    {
      label: 'Promedio de la Industria',
      data: [65, 59, 51, 49, 56, 55, 63, 69, 72, 64, 66, 69],
      borderColor: 'rgba(75, 192, 192, 1)',
      yAxisID: 'y-axis-1',
    },
    {
      label: 'Progreso de la Empresa',
      data: [28, 32, 38, 45, 36, 41, 61, 69, 58, 65, 70, 73],
      borderColor: 'rgba(153, 102, 255, 1)',
      yAxisID: 'y-axis-2',
    },
  ],
})

const chartOptions2 = ref({
  responsive: true,
  interaction: {
    mode: 'index' as const,
    intersect: false,
  },
  stacked: false,
  plugins: {
    title: {
      display: true,
      text: 'Promedio de la Industria vs. Progreso de la Empresa - Multi Eje',
    },
  },
  scales: {
    'y-axis-1': {
      type: 'linear',
      position: 'left',
    },
    'y-axis-2': {
      type: 'linear',
      position: 'right',
      grid: {
        drawOnChartArea: false,
      },
    },
  },

  onClick: handleClick2,
})

const chartData3 = ref({
  labels: [
    'Identificar',
    'Proteger',
    'Detectar',
    'Responder',
    'Recuperar',
    'Gobernar',
  ],
  datasets: [
    {
      label: 'Perfil Inicial',
      data: [28, 48, 40, 19, 96, 27],
      fill: true,
      backgroundColor: 'rgba(255, 99, 132, 0.2)',
      borderColor: 'rgb(255, 99, 132)',
      pointBackgroundColor: 'rgb(255, 99, 132)',
      pointBorderColor: '#fff',
      pointHoverBackgroundColor: '#fff',
      pointHoverBorderColor: 'rgb(255, 99, 132)',
    },
    {
      label: 'Perfil Actual',
      data: [65, 59, 71, 37, 81, 55],
      fill: true,
      backgroundColor: 'rgba(54, 162, 235, 0.2)',
      borderColor: 'rgb(54, 162, 235)',
      pointBackgroundColor: 'rgb(54, 162, 235)',
      pointBorderColor: '#fff',
      pointHoverBackgroundColor: '#fff',
      pointHoverBorderColor: 'rgb(54, 162, 235)',
    },
    {
      label: 'Perfil Recomendado',
      data: [80, 90, 85, 70, 90, 80],
      fill: true,
      backgroundColor: 'rgba(75, 192, 192, 0.2)',
      borderColor: 'rgb(75, 192, 192)',
      pointBackgroundColor: 'rgb(75, 192, 192)',
      pointBorderColor: '#fff',
      pointHoverBackgroundColor: '#fff',
      pointHoverBorderColor: 'rgb(75, 192, 192)',
    },
  ],
})

const chartOptions3 = ref({
  responsive: true,
  plugins: {
    legend: {
      position: 'top',
    },
    title: {
      display: true,
      text: 'Áreas de Mejora - Gráfico de Radar',
    },
  },
  scales: {
    r: {
      angleLines: {
        display: true,
      },
      suggestedMin: 0,
      suggestedMax: 100,
    },
  },
  onClick: handleClick3,
})

const chartData = ref({
  labels: ['Agosto', 'Septiembre', 'Octubre'],
  datasets: [
    {
      label: 'Auditorías de Cumplimiento',
      backgroundColor: '#7fb3d5',
      data: [50, 30, 22],
    },
    {
      label: 'Gestión de Riesgos de Terceros',
      backgroundColor: '#f87979',
      data: [40, 20, 12],
    },
    {
      label: 'Gestión de Vulnerabilidades',
      backgroundColor: '#f8d579',
      data: [60, 40, 32],
    },
    {
      label: 'Pruebas de Penetración',
      backgroundColor: '#4caf50',
      data: [70, 50, 42],
    },
  ],
})

const chartOptions = ref({
  responsive: true,
  plugins: {
    legend: {
      position: 'top',
    },
    title: {
      display: true,
      text: 'Indicadores de trabajo último trimestre - Gráfico de Barras',
    },
  },
})

const profileData = ref('')
const profile = ref('')
const isOpen = ref(false)

function setIsOpen(value: boolean) {
  console.log('setIsOpen', value)

  isOpen.value = value
}
</script>
