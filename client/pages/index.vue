<template lang="pug">
  div
    .top-right.links.d-none
      template(v-if="authenticated")
        router-link(:to="{ name: 'profile' }")
          | {{ $t('profile') }}
      template(v-else)
        router-link(:to="{ name: 'login' }")
          | {{ $t('login') }}
        router-link(:to="{ name: 'register' }")
          | {{ $t('register') }}

    .text-center
      .title.mb-4
        H1 {{ $t('project_name') }}
          br
          small {{ $t('main_page') }}

</template>

<script>
import { mapGetters } from 'vuex'

export default {
  // layout: 'simple',

  head () {
    return {
      title: this.$t('main_page'),
      description: 'testtesttest'
    }
  },

  data: () => ({
    title: process.env.appName
  }),

  computed: mapGetters({
    authenticated: 'auth/check'
  })
}
</script>

<style scoped>
.top-right {
  position: absolute;
  right: 10px;
  top: 18px;
}
</style>
