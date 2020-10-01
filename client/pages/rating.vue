<template lang="pug" lang="pug">
  div
    | {{ $t('rating') }}
</template>

<script>
export default {
  middleware: 'auth',

  head () {
    return { title: this.$t('rating') + ' | ' + this.$t('project_name') }
  }
}
</script>

<style scoped lang="stylus">

</style>
