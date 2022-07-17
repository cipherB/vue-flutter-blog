<template>
  <LatestArticle :article="articles[0]" />
  <section id="articles-section">
    <div :key="article.id" v-for="article in articles" >
      <BlogArticle :article="article" />
    </div>
  </section>
  <JoinUs />
</template>

<script>
import BlogArticle from '@/components/BlogArticle'
import LatestArticle from '@/components/LatestArticle'
import JoinUs from '@/components/JoinUs'

export default {
  name: 'HomePage',
  props: {
    articles: Array
  },
  components: {
    BlogArticle,
    LatestArticle,
    JoinUs
  }
}
</script>
<style lang="scss" scoped>
#articles-section {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  column-gap: 57px;
  row-gap: 48px;

  @media (max-width: 768px) {
    grid-template-columns: repeat(1, 1fr);
    row-gap: 16px;
  }
}
</style>