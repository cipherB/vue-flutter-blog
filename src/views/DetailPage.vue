<template>
  <article id="single-article" >
    <div  id="single-article__row1">
      <p id="single-article__row1-author">By {{article.parsely.meta.author[0].name}}</p>
      <p>2 Month Ago</p>
    </div>
    <h1 v-html="article.parsely.meta.headline" ></h1>
    <p v-html="article.content.rendered" id="single-article__content" ></p>
    <h3>More Articles</h3>
    <section id="single-article__articles">
      <BlogArticle :article="articles[Math.floor(Math.random() * articles.length)]" />
      <BlogArticle :article="articles[Math.floor(Math.random() * articles.length)]" />
      <BlogArticle :article="articles[Math.floor(Math.random() * articles.length)]" />
    </section>
  </article>
</template>

<script>
import axios from 'axios'
import BlogArticle from '@/components/BlogArticle'

export default {
  name: "DetailPage",
  props: {
    articles: Array
  },
  components: {
    BlogArticle
  },
  data() {
    return {
      article: []
    }
  },
  methods: {
    async fetchArticle(id) {
      let config = {
        headers: {
          'Accept': 'application/json'
        }
      }
      try {
        const articles = await axios.get(`https://techcrunch.com/wp-json/wp/v2/posts/${id}`, config)
        return articles.data
      } catch (err) {
        console.log(err)
      }
    }
  },
  async created() {
    this.article = await this.fetchArticle(this.$route.params.id)
  }
}
</script>
<style lang="scss" scoped>
h1 {
  font-size: 32px;
  font-weight: 900;
  margin: 0 0 23px 0;
}

h3 {
  font-size: 24px;
  font-weight: 900;
  margin-bottom: 23px;
}
#single-article {
  margin: 52px 0;
  padding: 0 200px;

  @media (max-width: 768px) {
    padding: 0 10px;
  }

  &__row1 {
    margin-bottom: 10px;
    font-size: 12px;
    display: flex;
    gap: 4px;

    &-author {
      color: #4B4B4B;
    }
  }
  &__content {
    margin-bottom: 46px;
    width: 100%;
    overflow-x: auto;

    // > img {
    //   width: 100%;

    // }
  }
  &__articles {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    column-gap: 47px;

    @media (max-width: 768px) {
      grid-template-columns: repeat(1, 1fr);
    }
  }
}
</style>
