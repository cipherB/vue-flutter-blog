<template>
  <article id="article-post" v-if="typeof article !== 'undefined'" >
    <router-link 
      :to="{path: `/detail/${article.id}/${article.slug}`}" 
      style="cursor:pointer"
    >
      <img :src="article.jetpack_featured_media_url" :alt="article.slug" id="article-post__img"/>
    </router-link>
    <div id="article-post__row1">
      <p id="article-post__row1-cat" >News Article</p>
      <span style="padding-bottom:4px" >.</span>
      <p id="article-post__row1-pub">1 Hour ago</p>
    </div>
    <h5 v-html="article.parsely.meta.headline"></h5>
    <p v-html="article.excerpt.rendered" id="article-post-excerpt" ></p>
    <div id="article-post__ex">
      <p id="article-post__ex-read" >3 Min Read</p>
      <router-link 
        :to="{path: `/detail/${article.id}/${article.slug}`}" 
        id="article-post__ex-detail"
      >
        Read Full
        <img src="../assets/arrow.svg" alt="arrow" />
      </router-link>
    </div>
  </article>
</template>

<script>
export default {
  name: 'BlogArticle',
  props: {
    article: Object,
  }
}
</script>
<style lang="scss" scoped>
h5 {
  font-size: 18px;
  font-weight: 700;
  margin: 0 0 8px 0;
}  

#article-post {
  width: 100%;
  min-height: 402px;
  padding: 10px;
  border: 1px solid #F5F5F5;
  border-radius: 5px;
  margin-bottom: 156px;

  &__img {
    width: 100%;
    height: 200px;
    margin-bottom: 16px;
  }

  &__row1 {
    display: flex;
    align-items: center;
    gap: 4px;
    margin-bottom: 8px;

    &-cat {
      font-size: 12px;
      color: #4B4B4B;
      font-weight: 500;
      margin: 0;
    }

    &-pub {
      font-size: 12px;
      font-weight: 500;
      margin: 0;
    }
  }
  &-excerpt {
    margin: 0 0 22px 0;
  }
  &__ex {
    display: flex;
    justify-content: space-between;

    &-read {
      font-size: 12px;
      font-weight: 500;
    }

    &-detail {
      display: flex;
      align-items: center;
      gap: 4px;
      font-size: 12px;
      font-weight: 700;
      color: #1473E6;
      cursor: pointer;
      text-decoration: none;
    }
  }
}
</style>