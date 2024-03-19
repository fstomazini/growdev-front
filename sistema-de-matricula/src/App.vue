<template>
  <v-app>
    <v-layout>
      <v-navigation-drawer
        image="https://cdn.vuetifyjs.com/images/backgrounds/bg-2.jpg"
        theme="dark"
        permanent
      >
        <v-list nav>
          <v-list-item prepend-icon="mdi-email" title="Alunos" value="Alunos"></v-list-item>
          <v-list-item prepend-icon="mdi-account-supervisor-circle" title="Supervisors" value="supervisors"></v-list-item>
          <v-list-item prepend-icon="mdi-clock-start" title="Clock-in" value="clockin"></v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-main>
        <Home />
      </v-main>
    </v-layout>
    

    <AppFooter />
  </v-app>
</template>

<script  setup>
  import Home from '@/components/Home.vue'
</script>
