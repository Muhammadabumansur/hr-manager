<template>
      <table class="table table-striped">
        <thead class="thead-dark">
          <tr>
            <th v-for="(col, index) in cols" :key="index">
              {{ col }}
            </th>
          </tr>
        </thead>
        <tr v-for="(applicant, index) in applicants" :key="index">
          <td v-for="(value, index) in applicants[index]" :key="index">{{ value }}</td>
        </tr>
      </table>
</template>

<script>
export default {
  props: ['applicants', 'cols'],
  data() {
    return {};
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>
