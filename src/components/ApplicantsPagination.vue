<template>
  <nav>
    <select class="form-control" name="" id="" @change="onChange($event)">
      <option value="10" selected>10</option>
      <option value="20">20</option>
      <option value="30">30</option>
    </select>
    <ul class="pagination">
      <li v-for="(item, index) in pagesQuantity" :key="index">
        <a href="" @click.prevent="onClick(index)">
          {{ index + 1 }}
        </a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  props: ['showNumber', 'pagesQuantity'],
  data() {
    return {

    };
  },
  methods: {
    onChange(event) {
      let num = Number(event.target.value);
      this.$emit('changeNumber', num)
    },
    onClick(index) {
      this.$emit('changePage', index)
    }
  }
};
</script>

<style>

</style>

