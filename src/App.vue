<template>
  <v-app>
    <v-app-bar app color="primary" dark class="title"
      >Table information</v-app-bar
    >
    <v-main>
      <TableInfo v-bind:listData="listData" />
    </v-main>
  </v-app>
</template>
<script>
import TableInfo from "./components/Table/TableInfor.vue";
export default {
  name: "App",
  components: {
    TableInfo,
  },
  data: () => ({
    listData: [
      { id: 1, name: "Banh Gio", number: "A123", price: 20000 },
      { id: 2, name: "Banh Xeo", number: "A456", price: 20000 },
      { id: 3, name: "Banh U", number: "A789", price: 20000 },
      { id: 4, name: "Banh Mi", number: "B123", price: 20000 },
      { id: 5, name: "Banh Ud", number: "B456", price: 20000 },
      { id: 6, name: "Banh Chuoi Chien", number: "B789", price: 20000 },
      { id: 7, name: "Banh Khoai", number: "C123", price: 20000 },
      { id: 8, name: "Banh Uot", number: "C456", price: 20000 },
      { id: 9, name: "Banh Khot", number: "C789", price: 20000 },
      { id: 10, name: "Banh Da Lon", number: "D123", price: 20000 },
    ],
  }),
};
</script>
<style scoped>
.title {
  display: flex;
  justify-content: center;
}
</style>
