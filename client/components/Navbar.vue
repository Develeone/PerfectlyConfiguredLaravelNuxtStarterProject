<template lang="pug">
  nav.navbar.navbar-expand-lg.navbar-light.bg-white
    .container.items-stretch.h-100
      button.navbar-toggler(:aria-label="$t('toggle_navigation')" type="button"
              data-toggle="collapse" data-target="#navbarToggler"
              aria-controls="navbarToggler" aria-expanded="false" )
        span.navbar-toggler-icon

      #navbarToggler.collapse.navbar-collapse.h-100

        ul.navbar-nav.h-100
          router-link.navbar-brand.h-100(:to="{ name: 'index' }")
            img.logo(src="/images/logo.svg" :alt="appName")

        ul.navbar-nav
          li.nav-item
            router-link.nav-link(:to="{ name: 'rating' }") {{ $t('rating') }}

        ul.navbar-nav.ml-auto
          // Authenticated
          li.nav-item.dropdown(v-if='user')
            a.nav-link.dropdown-toggle.text-dark(href='#' role='button' data-toggle='dropdown' aria-haspopup='true' aria-expanded='false')
              img.rounded-circle.profile-photo.mr-1(:src='user.photo_url')
              | {{ user.name }}
            .dropdown-menu
              router-link.dropdown-item.pl-3(:to="{ name: 'profile' }")
                fa(icon='user' fixed-width='')
                | {{ $t('personal_cabinet') }}
              .dropdown-divider
              router-link.dropdown-item.pl-3(:to="{ name: 'settings.profile' }")
                fa(icon='cog' fixed-width='')
                | {{ $t('settings') }}
              .dropdown-divider
              a.dropdown-item.pl-3(href='#' @click.prevent='logout')
                fa(icon='sign-out-alt' fixed-width='')
                | {{ $t('logout') }}

          // Guest
          template(v-else='')
            li.nav-item
              router-link.nav-link(:to="{ name: 'login' }" active-class='active')
                | {{ $t('login') }}
            li.nav-item
              router-link.nav-link(:to="{ name: 'register' }" active-class='active')
                | {{ $t('register') }}
</template>

<script>
import { mapGetters } from 'vuex'
import LocaleDropdown from './LocaleDropdown'

export default {
  components: {
    LocaleDropdown
  },

  data: () => ({
    appName: process.env.appName
  }),

  computed: mapGetters({
    user: 'auth/user'
  }),

  methods: {
    async logout () {
      // Log out the user.
      await this.$store.dispatch('auth/logout')

      // Redirect to login.
      this.$router.push({ name: 'login' })
    }
  }
}
</script>

<style scoped lang="stylus">
  .navbar
    height 56px

    .items-stretch
      align-items stretch

    .navbar-brand
      position relative
      padding 0

      .logo
        height 100%

    #navbarToggler
      .profile-photo
        width 2rem
        height 2rem
        margin -.375rem 0
</style>
