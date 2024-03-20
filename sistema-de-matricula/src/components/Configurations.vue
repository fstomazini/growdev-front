<template>
  <v-container fluid>
    <v-card fluid>
      <h1>Configurações</h1>
    </v-card>
    <v-divider> </v-divider>
    <v-card>
      <v-table>
        <v-row>
          <v-col>
            <v-chip class="ma-4 rounded-1 " variant="outlined">
              <h3>&nbsp;Tema&nbsp; </h3>
            </v-chip>
          </v-col>
          <v-col>
            <v-switch label="Modo Claro" @change="changeVisionMode"></v-switch>
          </v-col>
        </v-row>
      </v-table>
    </v-card>
  </v-container>
</template>
<script >
export default {
  data: () => ({}),
  methods: {
    changeVisionMode() {
      this.$emit('changeVisionMode')
    }
  }
}
</script>

