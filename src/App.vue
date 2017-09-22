<template>
  <div id="app">
    11144
    <pagination></pagination>
  </div>
</template>

<script>
import pagination from './component/pagination'
export default {
  name: 'app',
  data: () => {
    return {
      code: '',
      vcode: ''
    }
  },
  created: function () {
  },
  methods: {
  },
  components: {
    'pagination': pagination
  }
}
</script>

<style>
</style>
