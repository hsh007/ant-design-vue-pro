<template>
  <a-config-provider :locale="locale">
    <div id="app">
      <router-view/>
    </div>
  </a-config-provider>
</template>

<script>
import i18n from '@/locales'
import { AppDeviceEnquire } from '@/utils/mixin'
import { mixin } from '@/store/i18n-mixin'

export default {
  mixins: [AppDeviceEnquire, mixin],
  data () {
    return {
      locale: {}
    }
  },
  created () {
    this.$watch('currentLang', () => {
      this.locale = i18n.getLocaleMessage(this.currentLang).antLocale
    })
  }
}
</script>
