<template>
  <div class="query">
    <div class="query_table">
      <ms-table msg="Welcome to Your Vue.js App" />
      <ms-backtop msg="Welcome to Your Vue.js App" />
    </div>
  </div>
</template>

<script>
import TableQuery from "@/components/TableQuery.vue";
import Backtop from "@/components/Backtop.vue";

export default {
  name: "Query",
  components: {
    msTable: TableQuery,
    msBacktop: Backtop,
  },
};
</script>
