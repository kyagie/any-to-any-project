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

         <q-footer class="tt text-center">
        <q-toolbar>
          <q-toolbar-title>
            <a href="https://www.buymeacoffee.com/kyagie">Buy Me A Coffee.</a>
          </q-toolbar-title>
        </q-toolbar>
      </q-footer>
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
a{
    text-decoration: none;
    color: white;
}
</style>
