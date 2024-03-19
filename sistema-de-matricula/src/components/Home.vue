<template>
  <v-container class="fluid">
      <v-card fluid>
        <v-form>
          <v-row>
            <v-col cols="12" md="6">
             <v-text-field 
             v-model="search" 
             label="Digite sua busca">
             </v-text-field> 
            </v-col>
            <v-col cols="12" md="2">
             <v-btn > Buscar </v-btn>
            </v-col>
            <v-col cols="12" md="4">
             <v-btn > Cadastrar Aluno </v-btn>
            </v-col>
          </v-row>
        </v-form>
        <v-divider></v-divider>
        <v-table>
          <thead>
            <tr>
              <th class="text-left">
                Registro Acadêmico
              </th>
              <th class="text-left">
                Nome
              </th>
              <th class="text-left">
                CPF
              </th>
              <th class="text-left">
                Ações
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in students" :key="item.id">
              <td>{{item.id}}</td>
              <td>{{item.name}}</td>
              <td>{{item.cpf}}</td>
              <td>{{item.actions}}</td>
            </tr>
          </tbody>
        </v-table>
      </v-card>
      
  </v-container>
</template>

<script setup>
  //
</script>
<script>
  export default {
    data: () => ({
      students: [
        { id:'00000001' , name: "Felipe Tomazini", cpf: "000.000.000-00", actions:["editar" , "excluir"]  },
        { id:'00000002' , name: "Fulano de Tal", cpf: "000.000.000-00", actions:["editar" , "excluir"]  },
        { id:'00000003' , name: "Ciclano da Silva", cpf: "000.000.000-00", actions:["editar" , "excluir"]  },
        { id:'00000004' , name: "Tirano da Capadocia", cpf: "000.000.000-00", actions:["editar" , "excluir"]  }
      ],
    }),
  }
</script>