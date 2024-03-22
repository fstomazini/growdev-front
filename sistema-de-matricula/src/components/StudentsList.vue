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
            default : []
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
  watch:{
    
  }    
}
</script>
