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
           <transition
  appear
  enter-active-class="animated fadeIn"
  leave-active-class="animated fadeOut"
>
   <q-banner v-if="showAppInstallBanner" dense inline-actions  class="bg-white text-black">
      <b>Install this App?</b>
      <template v-slot:action>
        <q-btn @click="installApp" flat label="Yes" />
        <q-btn @click="showAppInstallBanner = false" flat label="Later" />
        <q-btn @click="nevershowAppInstallBanner"  flat label="Never" />

      </template>
    </q-banner>
    </transition>
        <q-toolbar>
          <q-toolbar-title>
            <a href="https://www.buymeacoffee.com/kyagie">Buy Me A Coffee. </a>
          </q-toolbar-title>
          
        </q-toolbar>
      </q-footer>
  </q-layout>
</template>

<script>
  let deferredPrompt;

export default {
  name: 'MainLayout',
  data () {
    return {
      showAppInstallBanner: false
    }
  },
  methods: {
    installApp(){
      this.showAppInstallBanner =false
      deferredPrompt.prompt();

      deferredPrompt.userChoice.then((choiceResult) => {
        if (choiceResult.outcome === 'accepted') {
        console.log('User said yes')
          this.nevershowAppInstallBanner()
        } else {
        console.log('User said no')
        }
      })
    },
    nevershowAppInstallBanner(){
        // console.log('User said never')
        this.showAppInstallBanner = false
        this.$q.localStorage.set('nevershowAppInstallBanner', true)
    }
  },
  mounted(){
    let nevershowAppInstallBanner = this.$q.localStorage.getItem('nevershowAppInstallBanner')

    if (!nevershowAppInstallBanner) {
       window.addEventListener('beforeinstallprompt', (e) => {
      e.preventDefault();

      deferredPrompt = e;
      setTimeout(() => {
      this.showAppInstallBanner = true
        
      }, 2500);
    })
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
