<template>
  <v-container class="fluid">
      <v-card class="d-flex  pa-2 justify-center" >
       <H1>Consulta de Alunos</H1> 
      </v-card>
      <v-divider></v-divider>
      <v-card fluid>
        <v-form>
          <v-row>
            <v-col cols="12" md="6">
             <v-text-field 
             v-model="search" 
             label="Digite sua busca">
             </v-text-field> 
            </v-col>
            <v-col cols="12" md="2" >
             <v-btn class="ma-4 pa-2"> Buscar </v-btn>
            </v-col>
            <v-col cols="12" md="4">
             <v-btn v-on:click="callRegistryStudents" class="ma-4 pa-2"> Cadastrar Aluno </v-btn>
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
              <td>
                {{item.id}}
                </td>
              <td>
                {{item.name}}
                </td>
              <td>
                {{item.cpf}}
                </td>
              <td>
                <v-row>
                  <v-col v-for="it in item.actions" :key="it.actionName">
                    <v-btn v-on:click="selectAction(it)">
                      {{it.actionName}}
                    </v-btn>
                  </v-col>
                </v-row>
              </td>
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
  import Request from '../services/request.js'
  export default {
    data: () => ({
      students: [],
    }),
    mounted: function (){
      this.getAllStudents();
    },
    methods:{
      callRegistryStudents(){
        this.$emit('callRegistryStudents');
      },
      callEditStudents(){
        this.$emit('callEditStudents');
      },
    getAllStudents(){
      let options = {
        request: {
          url: "http://localhost:7969/api/students",
        },  
      };
        let studentsList = []
        let actionEditar = {actionName : "Editar" , actionValue : "" };
        let actionExcluir = {actionName : "Excluir" , actionValue : "" };
        Request().getRequest(options).then( function(response){
          response.forEach(element => {
            actionEditar.actionValue = element.id;
            actionExcluir.actionValue = element.id;
            let item = {id : element.ra, name : element.name, cpf : element.cpf, actions: [actionEditar , actionExcluir]};
            studentsList.push(item);
          }); 
          
        });
        this.students = []
        this.students = studentsList;
        console.log(this.students)
        
    },
    selectAction(action){
      if(action.actionName == "Editar"){
        console.log("lancou editar")
      }
      else if(action.actionName == "Excluir"){
        console.log("lancou excluir")
      }
    },

    getAllStudents2(){
        let body = {
                title: this.newTitle,
                category: this.sendCategory,
                description: this.newDescription,
                priority: this.newPriority,
                situation: this.newSituation,
                limitDate: this.newLimitDate,
                annotations: this.newAnnotations,
            //    owner: Cookie.get('userId'),
        }
        let options = {
        request: {
          url: "http://localhost:3000/newtask",
          payload: body,
          extraOptions: {
              withCredentials: true,
              headers: {
               // 'Authorization': Cookie.get('jwt-token')
              }
            }
        },  
      };
        Request().postRequest(options);

    },

    },
    
  }
</script>


