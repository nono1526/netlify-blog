<template>
  <v-container class="vuetify__content">
    <v-card class="py-3 px-md-10 px-3 my-3" outlined tile>
      <Content slot-key="header"/>
      <div class="article-mate">
        <span>{{ formatDate }}</span>
        <v-icon small>mdi-folder</v-icon>
        <span class="text-right" v-for="(tag, i) in $page.frontmatter.tags" :key="i">
          {{ tag }}
        </span>
      </div>
      <Content/>
    </v-card>
    <v-card class="py-3 px-md-10 px-3 my-3" outlined tile>
      <ClientOnly>
        <Disqus
          :title="$page.title"
          :identifier="$page.regularPath"
          shortname="nono995" />
      </ClientOnly>
    </v-card>
  </v-container>
</template>

<script>
export default {
  methods: {
    getSiteOrigin () {
      return window.location.origin
    }
  },
  computed: {
    formatDate () {
      const date = new Date(this.$page.frontmatter.date)
      const dayMapping = ['日', '一', '二', '三', '四', '五', '六']
      return `${date.getFullYear()}年${date.getMonth() + 1}月${date.getDate()}日 星期${dayMapping[date.getDay()]}`
    }
  }
}
</script>

<style lang="sass">

</style>