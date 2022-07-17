<template>
  <article id="article" v-if="typeof article !== 'undefined'" >
    <router-link 
      :to="{path: `/detail/${article.id}/${article.slug}`}"
      style="cursor:pointer"
    >
      <img :src="article.jetpack_featured_media_url" :alt="article.slug" id="article__img"/>
    </router-link>
    <section id="article__element">
      <div id="article__element__row1" >
        <p id="article__element__row1-cat" >News Article</p>
        <p>.</p>
        <p id="article__element__row1-pub">1 Hour ago</p>
      </div>
      <h4 v-html="article.parsely.meta.headline" ></h4>
      <div id="article__element__row3" >
        <p v-html="article.excerpt.rendered" id="article__element__row3-excerpt" ></p>
        <div id="article__element__row3__ex">
          <p id="article__element__row3__ex-read" >3 Min Read</p>
          <router-link 
            :to="{path: `/detail/${article.id}/${article.slug}`}"
            id="article__element__row3__ex-detail"
          >
            Read Full
            <img src="../assets/arrow.svg" alt="arrow" />
          </router-link>
        </div>
      </div>
    </section>
  </article>
</template>

<script>
export default {
  name: 'LatestArticle',
  props: {
    article: Object
  }
}
</script>
<style lang="scss" scoped>
h4 {
  font-weight: 900;
  font-size: 22px;
  margin: 0;
}

#article{
  width: 100%;
  display: flex;
  gap: 15.5px;
  margin-bottom: 74px;

  @media (max-width: 768px) {
    flex-direction: column;
  }

  &__img {
    width: 500px;
    height: 280px;

    @media (max-width: 768px) {
      width: 100%;
    }
  }

  &__element {
    display: flex;
    flex-direction: column;
    gap: 8px;

    &__row1 {
      display: flex;
      align-items: center;
      gap: 4px;

      &-cat {
        font-size: 12px;
        color: #4B4B4B;
        font-weight: 700;
      }

      &-pub {
        font-size: 12px;
      }
    }

    &__row3 {
      display: flex;
      flex-direction: column;
      gap: 36px;

      &-excerpt {
        text-align: justify;
        margin: 0;
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
  }
}
</style>