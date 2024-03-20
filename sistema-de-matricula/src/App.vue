<template>
  <v-app>
    <v-layout>
    
      <v-navigation-drawer
        image="https://cdn.vuetifyjs.com/images/backgrounds/bg-2.jpg"
        theme="dark"
        permanent
      >
        <v-list nav>
          <v-list-item prepend-icon="mdi-account-supervisor-circle" title="Alunos" value="students" v-on:click="changeToStudantesPage"></v-list-item>
          <v-list-item prepend-icon="mdi-pencil" title="Configurações" value="configurations" v-on:click="changeToConfigsPage"></v-list-item>
          <v-list-item prepend-icon="mdi-close-circle" title="Sair" value="logout" v-on:click="triggerLogoutFunction"></v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-main>
        <Home 
          ref="home"
          @changeVisionMode="toggleTheme"
        />
      </v-main>
    </v-layout>
    

    <AppFooter />
  </v-app>
</template>

<script  setup>
  import Home from '@/components/Home.vue'
  import { useTheme } from 'vuetify'
  import { ref } from 'vue';
  var actualPage =  "studants"
  const theme = useTheme()
  const home = ref(null)

  
  function toggleTheme() {
    theme.global.name.value = theme.global.current.value.dark ? 'light' : 'dark'
  }
  function changeToStudantesPage() {
    home.value.callStudentsView();
  }
  function changeToConfigsPage() {
    home.value.callConfigurationView()
  }

</script>
