<template>
  <div
    class="w-full max-w-6xl mx-auto rounded-2xl py-10 lg:px-10 md:px-10 px-3 bg-gradient-to-r from-[#0644A6] to-[#0063E7] text-white shadow-lg"
  >
    <!-- Top Text -->
    <h2 class="text-2xl md:text-3xl lg:px-0 md:px-0 px-18 font-semibold text-center mb-6 text-white">
      <span class="font-bold">15 million</span> searches and counting
    </h2>

    <!-- Search Form -->
    <div class="flex flex-col md:flex-row items-start md:items-center gap-4 relative px-20">
      <!-- Search Input with icon -->
      <div class="relative w-full md:flex-1" ref="inputWrap">
        <div class="flex items-center bg-white rounded-[8px] px-3 py-2">
          <MagnifyingGlassIcon class="w-5 h-5 text-gray-500 mr-2" />
          <input
            ref="searchInput"
            type="text"
            placeholder="What would you like to study? (e.g., law)"
            class="w-full bg-transparent text-black placeholder-gray-500 focus:outline-none"
            v-model="query"
            @focus="open = true"
            @keydown.down.prevent="move(1)"
            @keydown.up.prevent="move(-1)"
            @keydown.enter.prevent="selectHighlighted"
            @keydown.esc.prevent="open = false"
          />
        </div>

        <!-- Autocomplete Dropdown -->
        <ul
          v-if="open && filteredPrograms.length > 0"
          class="absolute top-full mt-1 w-full bg-white text-black rounded-[8px] shadow-md z-10 max-h-60 overflow-y-auto"
        >
          <li
            v-for="(program, idx) in filteredPrograms"
            :key="program.id"
            class="px-4 py-2 cursor-pointer"
            :class="idx === highlight ? 'bg-gray-100' : 'hover:bg-gray-100'"
            @mousedown.prevent="handleOptionClick(program.name)"
            @mousemove="highlight = idx"
          >
            {{ program.name }}
          </li>
        </ul>
      </div>

      <!-- Country Select with icon -->
      <div class="flex items-center w-full md:w-1/3 bg-white rounded-[8px] px-3 py-[10px]">
        <GlobeAltIcon class="w-5 h-5 text-gray-500 mr-2" />
        <select v-model="country" class="w-full bg-transparent text-black focus:outline-none">
          <option value="canada">Canada</option>
          <option value="uk">United Kingdom</option>
          <option value="usa">United States</option>
          <option value="australia">Australia</option>
        </select>
      </div>

      <!-- Search Button -->
      <button
        class="w-full md:w-auto bg-white text-[#3985e7] font-semibold px-8 py-[9px] rounded-[8px] hover:bg-gray-100 transition"
        @click="submit"
      >
        Search
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onBeforeUnmount } from 'vue'
import { MagnifyingGlassIcon, GlobeAltIcon } from '@heroicons/vue/24/outline'

const studyPrograms = [
  { id: 1, name: 'International Business' },
  { id: 2, name: 'Computer Science' },
  { id: 3, name: 'Mechanical Engineering' },
  { id: 4, name: 'Artificial Intelligence' },
  { id: 5, name: 'Marketing and Management' },
  { id: 6, name: 'Psychology' },
  { id: 7, name: 'Biomedical Sciences' },
  { id: 8, name: 'Finance and Accounting' },
  { id: 9, name: 'Economics' },
  { id: 10, name: 'Law' },
  { id: 11, name: 'Data Science' },
  { id: 12, name: 'Architecture' },
  { id: 13, name: 'Civil Engineering' },
  { id: 14, name: 'Environmental Studies' },
  { id: 15, name: 'Graphic Design' },
]

const query = ref('')
const country = ref('canada')
const open = ref(false)
const highlight = ref(-1) // highlighted index for keyboard nav
const inputWrap = ref(null)
const searchInput = ref(null)

const filteredPrograms = computed(() => {
  if (!query.value) return []
  const q = query.value.toLowerCase()
  return studyPrograms.filter(p => p.name.toLowerCase().includes(q)).slice(0, 5)
})

function handleOptionClick(name) {
  query.value = name
  open.value = false
  highlight.value = -1
}

function move(dir) {
  if (!open.value) open.value = true
  const len = filteredPrograms.value.length
  if (len === 0) return
  highlight.value = (highlight.value + dir + len) % len
}

function selectHighlighted() {
  if (highlight.value < 0) return
  const item = filteredPrograms.value[highlight.value]
  if (item) handleOptionClick(item.name)
}

function onClickOutside(e) {
  if (!inputWrap.value) return
  if (!inputWrap.value.contains(e.target)) {
    open.value = false
    highlight.value = -1
  }
}

function submit() {
  // Do whatever search action you want (navigate, call API, etc.)
  // Example: navigate with query params
  // navigateTo({ path: '/search', query: { q: query.value, country: country.value } })
  console.log('Search:', { q: query.value, country: country.value })
}

onMounted(() => {
  document.addEventListener('click', onClickOutside)
})
onBeforeUnmount(() => {
  document.removeEventListener('click', onClickOutside)
})
</script>
