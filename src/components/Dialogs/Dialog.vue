<template>
  <div>
    <v-row justify="center">
      <v-dialog v-model="isOpenDialog" scrollable max-width="300px">
        <v-card>
          <v-card-title>Select Opinion</v-card-title>
          <v-divider></v-divider>
          <v-card-text style="height: 300px;">
            <v-radio-group v-model="text" column>
              <v-radio label="Very Tasty" value="Very Tasty"></v-radio>
              <v-radio label="Delicious" value="Delicious"></v-radio>
              <v-radio label="Normal" value="Normal"></v-radio>
              <v-radio label="Inedible" value="Inedible"></v-radio>
              <v-radio label="Bad" value="Bad"></v-radio>
              <v-radio label="Very Bad" value="Very Bad"></v-radio>
            </v-radio-group>
          </v-card-text>
          <v-divider></v-divider>
          <v-card-actions>
            <v-btn color="blue darken-1" text @click="onCloseDialog">
              Close
            </v-btn>
            <v-btn color="blue darken-1" text v-on:click="handleCheckbox">
              Save
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
    <ModalInfo
      v-bind:isOpenModal="isOpenModal"
      v-if="isOpenModal"
      v-bind:text="text"
      v-bind:itemId="itemId"
      @onCloseModal="onCloseDialog"
    ></ModalInfo>
  </div>
</template>
<script>
import ModalInfo from "../Modal/ModalInfo.vue";
export default {
  props: {
    isOpenDialog: Boolean,
    itemId: { type: [String, Number], default: null },
  },
  components: {
    ModalInfo,
  },
  data() {
    return {
      text: "",
      isOpenModal: false,
    };
  },
  methods: {
    onCloseDialog() {
      this.$emit("onCloseDialog");
    },
    handleCheckbox() {
      this.isOpenModal = true;
    },
  },
};
</script>
