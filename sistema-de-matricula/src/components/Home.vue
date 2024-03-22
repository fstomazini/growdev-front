<template>
  <v-container>
    <v-header>

    </v-header>
    <div v-if="isStudentsList">
      <StudentsView @callRegistryStudents="callRegistryStudents" />
    </div>
    <div v-if="isNewStudent">
      <StudentForm @callStudentsView="callStudentsView" />
    </div>
    <div v-if="isConfig">
      <Configurations @changeVisionMode="changeVisionMode" />
    </div>
    <div v-if="isEdit">
      <StudentEditForm @changeVisionMode="callEditStudent" />
    </div>
  </v-container>
</template>

<script setup>
import { defineAsyncComponent } from 'vue'

const AsyncComp = defineAsyncComponent(() =>
  import('../components/StudentsView.vue')
)
</script>
<script>
export default {
  props: {
    actualPage: {
      type: String,
      default: ''
    }
  },
  data: () => ({
    isStudentsList: true,
    isNewStudent: false,
    isConfig: false,
    isEdit: false
  }),
  expose: ['callConfigurationView', 'callStudentsView'],
  methods: {
    callRegistryStudents() {
      ;(this.isStudentsList = false), (this.isNewStudent = true), (this.isConfig = false), (this.isEdit = false)
    },
    callStudentsView() {
      ;(this.isStudentsList = true), (this.isNewStudent = false), (this.isConfig = false), (this.isEdit = false)
    },
    callConfigurationView() {
      ;(this.isStudentsList = false), (this.isNewStudent = false), (this.isConfig = true), (this.isEdit = false)
    },
    callEditStudants() {
      ;(this.isStudentsList = false), (this.isNewStudent = false), (this.isConfig = false), (this.isEdit = tru)
    },
    changeVisionMode() {
      this.$emit('changeVisionMode')
    }
  }
}
</script>