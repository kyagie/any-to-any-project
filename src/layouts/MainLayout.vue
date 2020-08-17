<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-toolbar-title class="text-center tt">
          Any To Any
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

export default {
  name: 'MainLayout',
  data () {
    return {
    }
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Alata&display=swap');
.tt{
    font-family: 'Alata', sans-serif;
}
</style>
