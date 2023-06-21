<template>

<h1>Listado de usuarios</h1>
<input type="text" placeholder="Buscar users" v-model="search" @keyup="handleSearch"/>
<div>
  <button @click="handleLayout(ListLayout)">Ver lista</button>
  <button @click="handleLayout(CardLayout)">Ver tarjetas</button>
  <button @click="handleLayout(TableLayout)">Ver tabla</button>
</div>
<component :is="layout" :content="filteredUsers" />

</template>

<script lang="ts" setup>
import { ref, defineAsyncComponent } from 'vue'

const ListLayout = defineAsyncComponent(() => import('@/layouts/ListLayout.vue'))
const TableLayout = defineAsyncComponent(() => import('@/layouts/TableLayout.vue'))
const CardLayout = defineAsyncComponent(() => import('@/layouts/CardLayout.vue'))

const layout = ref(ListLayout)

const handleLayout = (cmp:any) => layout.value = cmp

const search = ref('')

const handleSearch = () => {
  filteredUsers.value = users.value.filter(item => item.name.toLowerCase().includes(search.value.toLowerCase()))
}

const users = ref([
  {
    name: "Zenen",
    age: "45",
    position: "full stack"
  },
  {
    name: "Alexis",
    age: "34",
    position: "frontend"
  },
  {
    name: "Irama",
    age: "43",
    position: "backend"
  },
  {
    name: "Isabelsi",
    age: "9",
    position: "Css"
  },
  {
    name: "Francisco",
    age: "7",
    position: "html"
  },
  {
    name: "Jose",
    age: "6",
    position: "js"
  },
  {
    name: "Jauna",
    age: "60",
    position: "full stack"
  },
  {
    name: "Mama",
    age: "45",
    position: "developer"
  }
  ])

  const filteredUsers:any = ref([])

  filteredUsers.value = users.value
</script>

<style scoped>

</style>
