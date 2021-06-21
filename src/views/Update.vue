<template>
  <div class="update">
    <ms-table msg="Welcome to Your Vue.js App" />
    <ms-backtop msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import TableUpdate from "@/components/TableUpdate.vue";
import Backtop from "@/components/Backtop.vue";

export default {
  name: "Update",
  components: {
    msTable: TableUpdate,
    msBacktop: Backtop,
  },
};
</script>