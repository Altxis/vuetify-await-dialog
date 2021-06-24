<template>
  <v-container>
    <v-textarea :value="textareaText" readonly></v-textarea>
    <v-btn @click="showDialog">Do it!</v-btn>
    <AwaitDialog
      title="Поставить галку?"
      description="Вы прям уверены?"
      ref="dialog"
    />
  </v-container>
</template>

<script>
import AwaitDialog from '../components/AwaitDialog.vue'

export default {
  components: {
    AwaitDialog,
  },
  data() {
    return {
      textareaText: '',
    }
  },
  methods: {
    async showDialog() {
      ;(await this.$refs.dialog.open())
        ? (this.textareaText += 'Yes selected!\n')
        : (this.textareaText += 'No selected!\n')
    },
  },
}
</script>
