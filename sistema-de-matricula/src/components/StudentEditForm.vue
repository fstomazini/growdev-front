<template>
    <v-container fluid>
        <v-card>
            <H1>Cadastro de Alunos</H1>
        </v-card>
        <v-divider></v-divider>
        <v-card>
            <v-table>
                <v-row>
                    <v-col cols="12" md="2">
                            <v-chip class="ma-4 rounded-1">
                                <h2>Nome</h2>
                            </v-chip>
                    </v-col>
                    <v-col cols="12" md="10">
                        <v-text-field 
                            v-model="editedStudent.name" 
                            label="Nome">
                        </v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col cols="12" md="2">
                        <v-chip class="ma-4 rounded-1">
                            <h2>E-mail</h2>
                        </v-chip>
                    </v-col>
                    <v-col cols="12" md="10">
                        <v-text-field 
                            v-model="editedStudent.email" 
                            label="E-mail">
                        </v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col cols="12" md="2">
                        <v-chip class="ma-4 rounded-1">
                            <h2>&nbsp;RA&nbsp;</h2>
                        </v-chip>
                    </v-col>
                    <v-col cols="12" md="10">
                        <v-text-field 
                            v-model="editedStudent.ra" 
                            label="RA">
                        </v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col cols="12" md="2">
                        <v-chip class="ma-4 rounded-1">
                            <h2>CPF</h2>
                        </v-chip>
                    </v-col>
                    <v-col cols="12" md="10">
                        <v-text-field 
                            v-model="editedStudent.cpf" 
                            label="CPF">
                        </v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col cols="12" md="8">
                        
                    </v-col>
                    <v-col cols="12" md="2">
                        <v-btn v-on:click="callStudentsView">Cancelar</v-btn>
                    </v-col>
                    <v-col cols="12" md="2">
                        <v-btn v-on:click="saveStudendData">Salvar</v-btn>
                    </v-col>
                </v-row>
            </v-table>
        </v-card>
    </v-container>
</template>
<script setup>
  
</script>
<script>
    import Request from "@/services/request.js"
    export default {
    props:{
        studentId:{
            type : String,
            required : true,
        }
    },    
    data: () => ({     
        EditedStudent : {
        nome:"",
        email:"",
        cpf:"",
        ra:"",
      },
    
  }),

  methods:{
    getStudent(id){
      var ref = this
      let options = {
        request: {
          url: "http://localhost:7969/api/students/"+studentId,
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
      saveStudendData(){
        
        this.callStudentsView();
      },  
      callStudentsView(){
        
        this.$emit('callStudentsView');
      }
    },
  }

</script>
