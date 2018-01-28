<template>
  <form action="" class="form-inline">
    <input type="text">
    <input type="text">
    <select name="" id="">
      <option v-for="(country, index) in countries" value="" :key="index"> {{ country }} </option>
    </select>
    <div class="checkbox">
      <label v-for="(skill, index) in skills" :key="index">
        <input type="checkbox" :value="skill" v-model="skillsObject[skill]"> {{ skill }}
      </label>
    </div>
  </form>
</template>

<script>
export default {
  props: ['skillsObject', 'countries'],
  data() {
    return {
      skills: ['Vue', 'React', 'Angular'],
    };
  },
};
</script>

<style>

</style>

