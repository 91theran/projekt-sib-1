<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Projekt SIB
        </q-toolbar-title>
    
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Sidor
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import EssentialLink from 'components/EssentialLink.vue'
import { ref } from 'vue'

const linksList = [
  {
    title: 'Formulär',    
    icon: 'school',
    link: '/form'
  },
  {
    title: 'Statistik',    
    icon: 'code',
    link: '/statistics'
  },
];


const leftDrawerOpen = ref(false)

  
const essentialLinks = ref(linksList)
  
function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value
}

</script>
