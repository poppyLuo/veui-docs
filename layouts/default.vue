<template>
<main
  :class="{
    'post-layout': true,
    'no-links': !hasFooterLinks
  }"
>
  <one-header/>
  <one-menu :nav="nav"/>
  <nuxt/>
  <one-footer
    class="footer"
    :nav="nav"
    @update="updateLayout"
  />
  <one-back-to-top/>
</main>
</template>

<script>
import 'focus-visible'
import OneHeader from '../components/OneHeader'
import OneMenu from '../components/OneMenu'
import OneFooter from '../components/OneFooter'
import OneBackToTop from '../components/OneBackToTop'
import nav from '../assets/data/nav.json'
import i18n from '../common/i18n'
import i18nMgr from 'veui/managers/i18n'

export default {
  name: 'main-doc',
  components: {
    OneHeader,
    OneMenu,
    OneFooter,
    OneBackToTop
  },
  mixins: [i18n],
  data () {
    return {
      hasFooterLinks: true
    }
  },
  computed: {
    nav () {
      return nav[this.locale]
    }
  },
  watch: {
    locale: {
      handler (val) {
        if (i18nMgr.locale !== val) {
          i18nMgr.locale = val
        }
        if (this.$i18n.locale !== val) {
          this.$i18n.locale = val
        }
        if (process.env.VUE_ENV !== 'server') {
          document.documentElement.setAttribute('lang', val)

          const { docsearchInstance } = window
          if (docsearchInstance) {
            docsearchInstance.autocomplete
              .eq(0)
              .data('aaAutocomplete')
              .dropdown.datasets[0].clearCachedSuggestions()
            docsearchInstance.client.clearCache()
            docsearchInstance.algoliaOptions.facetFilters = [`lang:${val}`]
          }
        }
      },
      immediate: true
    }
  },
  methods: {
    updateLayout ({ hasLinks }) {
      this.hasFooterLinks = hasLinks
    }
  }
}
</script>

<style lang="stylus" scoped>
$sidebar-width = 240px

main
  height 100%

.content
  margin-top 60px

.content, .footer
  max-width 1180px - $sidebar-width
  min-width 560px
  transition margin-left 0.5s cubic-bezier(0.785, 0.135, 0.15, 0.86)
</style>
