<script setup lang="ts">
import { ref, watch } from 'vue'

const valid = ref(false)
const text = ref('qqq')
const amount = ref(0)
const checkbox = ref(false)

const textRules = ref([
  (value: string) => {
    if (value) return true
    return 'Name is requred.'
  },
  (value: string) => {
    if (value?.length <= 10) return true
    return 'Name must be less than 10 characters.'
  }
])

watch(text, () => console.log(text.value))
</script>

<template>
  <v-form v-model="valid">
    <v-container fluid>
      <v-row>
        <v-col cols="12">
          <v-text-field
            v-model="text"
            :rules="textRules"
            label="First name"
            required
            hide-details
          ></v-text-field>
        </v-col>
        <v-col cols="12">
          <v-text-field
            type="number"
            v-model="amount"
            label="Amount"
            required
            hide-details
          ></v-text-field>
        </v-col>
      </v-row>
      <v-row cols="12" justify="space-between">
        <v-col cols="6" class="py-0">
          <v-checkbox
            v-model="checkbox"
            label="Запретить"
            color="primary"
            density="compact"
            hide-details
          />
        </v-col>
        <v-col cols="3">
          <v-btn variant="tonal" block> Add</v-btn>
        </v-col>
        <v-col cols="3">
          <v-btn variant="tonal" block> Save</v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<style scoped></style>
