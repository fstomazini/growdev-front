<template>
    <v-container>
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
          <tbody >
            <tr v-for="item in students" :key="item.id" >
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
                  <v-col v-for="it in item.actions" :key="it">
                    <v-btn v-on:click="selectAction(it)">
                      {{it.actionName}}
                    </v-btn>
                  </v-col>
                </v-row>
              </td>
            </tr>
          </tbody>
        </v-table>
    </v-container>
</template>
<script setup>

</script>
<script>
export default {
    props:{
        students : {
            type : Object,
            required : true,
            default : [{ id: "000000002", name: "andreia da costa", cpf: "000.000.000-01", actions : [{actionName:"Editar", actionValue: "000000002" },{actionName:"EXcluir", actionValue: "000000002"}]},
                       { id: "000000003", name: "vitor da costa", cpf: "000.000.000-02", actions : [{actionName:"Editar", actionValue: "000000003" },{actionName:"EXcluir", actionValue: "000000003"}]},
                       { id: "000000004", name: "Jonatan da costa", cpf: "000.000.000-03", actions : [{actionName:"Editar", actionValue: "000000004" },{actionName:"EXcluir", actionValue: "000000004"}]},
                       { id: "000000005", name: "joao da costa", cpf: "000.000.000-04", actions : [{actionName:"Editar", actionValue: "000000005" },{actionName:"EXcluir", actionValue: "000000005"}]}]
            }
    },
    data () {
      return {
        componentKey : 0
      }
    },
    methods:{
      forceRerender(){
        this.componentKey += 1;
      },
    selectAction(action){
        this.$emit('selectAction', action)
    },
  },
  computed:{
    haveChangesInStudents(){
      if(this.students.length > 0){
        console.log("é isso")

        return this.students ;
      }
    }
  }    
}
</script>
