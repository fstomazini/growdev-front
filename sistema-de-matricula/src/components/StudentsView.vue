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
        <StudentsList 
          :students="students"
          @selectAction="selectAction"
        />
      </v-card>
  </v-container>
</template>

<script setup>
  //
</script>
<script>
  import Request from '../services/request.js'


  export default {
    data () {
      return {
        students : [],
        componentKey : 0
      }
    },
    beforeMount: function (){
      this.getAllStudents();

    },
    methods:{
      forceRerender(){
        this.componentKey += 1;
      },
      callRegistryStudents(){
        this.$emit('callRegistryStudents');
      },
      callEditStudents(){
        this.$emit('callEditStudents');
      },
    getAllStudents(){
      var ref = this
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
        ref.students = studentsList;
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
  },    
}
</script>


