<template>
  <v-dialog v-model="dialog" :max-width="maxWidth" @click:outside="disagree">
    <v-card>
      <v-card-title class="headline">{{ title }}</v-card-title>
      <v-card-text>{{ description }}</v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="primary" text @click="agree">Да</v-btn>
        <v-btn color="primary" text @click="disagree">Нет</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  data() {
    return {
      resolve: () => {},
      reject: () => {},
      dialog: false,
    }
  },
  props: {
    title: String,
    description: String,
    maxWidth: {
      type: Number,
      default: 300,
    },
    yesButtonCaption: {
      type: String,
      default: 'Yes',
    },
    noButtonCaption: {
      type: String,
      default: 'No',
    },
  },
  methods: {
    open() {
      return new Promise(res => {
        this.dialog = true
        this.resolve = res
      })
    },
    agree() {
      this.dialog = false
      this.resolve(true)
    },
    disagree() {
      this.dialog = false
      this.resolve(false)
    },
  },
}
</script>
