<template>
    <v-container>
        <v-card class="d-flex  pa-2 justify-center">
            <H1>Login</H1>
        </v-card>
        <v-divider>
        </v-divider>
        <div class="d-flex ma-2 pa-2 justify-center">
            <v-card>
                <v-row>
                    <v-col cols="12" >
                        <v-text-field v-model="email" label="E-mail" :rules="emailRules">
                        </v-text-field>
                    </v-col>

                    <v-col cols="12" >
                        <v-text-field v-model="password" label="Password" >    
                        </v-text-field>
                    </v-col>
                    
                    <v-col cols="12" class="d-flex  pa-2 justify-center">
                        <v-btn>
                            Login
                        </v-btn>
                    </v-col>
                    <v-col cols="12" class="d-flex  pa-2 justify-center">
                        <v-btn>
                            Cadastrar
                        </v-btn>
                    </v-col>
                </v-row>
            </v-card>
        </div>
    </v-container>
</template>
<script>
  export default {
    data: () => ({
      valid: false,
      firstname: '',
      lastname: '',
      nameRules: [
        value => {
          if (value) return true

          return 'Name is required.'
        },
        value => {
          if (value?.length <= 10) return true

          return 'Name must be less than 10 characters.'
        },
      ],
      email: '',
      emailRules: [
        value => {
          if (value) return true

          return 'E-mail is requred.'
        },
        value => {
          if (/.+@.+\..+/.test(value)) return true

          return 'E-mail must be valid.'
        },
      ],
    }),
  }
</script>