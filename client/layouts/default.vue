<template lang="pug">
  .layout
    navbar

    .container.mt-4
      nuxt

    custom-footer
</template>

<script>
import CustomFooter from '../components/CustomFooter'
import LocaleDropdown from '~/components/LocaleDropdown'
import Navbar from '~/components/Navbar'

export default {
  components: {
    CustomFooter,
    LocaleDropdown,
    Navbar
  }
}
</script>
