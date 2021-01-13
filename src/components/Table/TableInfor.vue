<template>
  <div class="table">
    <v-simple-table>
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-left">
              ID
            </th>
            <th class="text-left">
              Vietnamese cakes
            </th>
            <th class="text-left">
              Number
            </th>
            <th class="text-left">
              Price
            </th>
            <th class="text-left">
              Comment
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in listData" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.number }}</td>
            <td>{{ changeType }}</td>
            <td>
              <button
                class="btn btn-icon btn-light btn-sm mx-3"
                @click="handleOpenDialog(item.id)"
                title="Update"
              >
                <v-icon large color="blue darken-2">
                  mdi-message-text
                </v-icon>
              </button>
            </td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
    <Dialog
      v-if="isOpenDialog"
      v-bind:isOpenDialog="isOpenDialog"
      @onCloseDialog="handleClose"
      v-bind:itemId="productId"
    ></Dialog>
  </div>
</template>
<script>
import Dialog from "../Dialogs/Dialog.vue";
export default {
  name: "table",
  props: {
    listData: {
      type: Array,
    },
  },
  components: {
    Dialog,
  },
  data() {
    return {
      isOpenDialog: false,
      productId: "",
    };
  },
  methods: {
    handleOpenDialog(productId) {
      this.productId = productId;
      this.isOpenDialog = true;
    },
    handleClose() {
      this.isOpenDialog = false;
    },
  },
  computed: {
    changeType() {
      let listData = this.listData;
      let result = [];
      for (let i = 0; i < listData.length; i++) {
        let newData = listData[i].price;
        let number = new Intl.NumberFormat("de-DE", {
          style: "currency",
          currency: "VND",
        }).format(newData);
        result.push(number);
      }
      return result[0];
    },
  },
};
</script>
