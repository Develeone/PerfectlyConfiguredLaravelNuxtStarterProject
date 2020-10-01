<template lang="pug" lang="pug">
  div
    | {{ $t('rating') }}
</template>

<script>
export default {
  middleware: 'auth',

  head () {
    return { title: this.$t('rating') }
  }
}
</script>

<style scoped lang="stylus">

</style>
