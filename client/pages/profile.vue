<template lang="pug">
  card(:title="$t('personal_cabinet')")
    | {{ $t('you_are_logged_in') }}

    div
      router-link(:to="{ name: 'index' }")
        | {{ $t('index') }}

    router-link.dropdown-item.pl-3(:to="{ name: 'settings.profile' }")
      fa(icon="cog" fixed-width)
      | {{ $t('settings') }}
</template>

<script>
export default {
  middleware: 'auth',

  head () {
    return { title: this.$t('profile') }
  }
}
</script>
