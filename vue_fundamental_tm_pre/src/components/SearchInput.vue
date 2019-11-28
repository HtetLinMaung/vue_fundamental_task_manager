<template>
  <input type="text" v-model="search" class="search" placeholder="search" />
</template>

<script>
export default {
  name: 'SearchInput',
  props: ['items', 'searchKeys'],
  data: () => ({
    search: ''
  }),
  watch: {
    search(newVal) {
      const { items, searchKeys } = this
      const re = new RegExp(newVal, 'i')

      const search_items = items.filter(item => {
        for (const [key, value] of Object.entries(item)) {
          if (
            searchKeys.some(searchKey => key == searchKey) &&
            `${value}`.match(re)
          ) {
            return true
          }
        }
      })

      this.$emit('search-filter', search_items)
    }
  }
}
</script>

<style scoped>
.search {
  font-size: 15px;
  padding: 0.3rem 0.8rem;
  color: rgb(117, 105, 105, 0.9);
  border-radius: 15px;
  border: 1px solid rgb(143, 137, 137);
  transition-property: border;
  transition-duration: 0.3s;
}
.search:focus {
  outline: none;
  border: 1px solid rgb(37, 221, 253);
}
</style>
