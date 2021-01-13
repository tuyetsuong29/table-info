<template>
  <v-dialog v-model="isOpenModal" scrollable max-width="500px">
    <v-card>
      <div class="formInfo">
        <v-card-text><b>ID:</b>{{ itemId }}</v-card-text>
        <v-card-text><b>Comment:</b> {{ text }}</v-card-text>
      </div>
      <v-card-actions class="button">
        <v-btn color="blue darken-1" text v-on:click="onCloseModal">
          Close
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>
<script>
export default {
  data() {
    return {};
  },
  props: {
    isOpenModal: { type: Boolean, default: null },
    itemId: { type: [String, Number], default: null },
    text: { type: [String, Number], default: null },
  },
  methods: {
    onCloseModal() {
      this.isOpenModal = false;
      this.$emit("onCloseModal");
    },
  },
};
</script>
<style scoped>
.formInfo {
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
}
.button {
  float: right;
}
</style>
