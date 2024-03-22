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
          <v-list-item prepend-icon="mdi-close-circle" title="Sair" value="logout" v-on:click="loggedOff" v-show="isLogged"></v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-main>
        <div v-if="isLogged">
          <Home 
          ref="home"
          @changeVisionMode="toggleTheme"
          @loggedOff="loggedOff"
        />
        </div>
        <div v-else-if="isRegistry">
          <RegistryPage />
        </div>
        <div v-else>
          <LoginPage 
            @loggedIn="loggedIn"
            @registry="registry"
          />
        </div>
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
<script>

export default {
  data () {
      return {
        isLogged : false,
        isRegistry: false
      }
    },
    methods:{
      //this login methods are place holders to future login service with jwt and proper security
      loggedIn(){
        this.isLogged = true
        this.isRegistry = false
      },
      registry(){
        this.isLogged = false
        this.isRegistry = true
      },
      loggedOff(){
        this.isLogged = false
        this.isRegistry = false
      }
    }
}
</script>

