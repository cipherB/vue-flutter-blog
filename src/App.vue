<template>
  <div id="container" >
    <NavBar />
    <router-view :articles="articles" ></router-view>
  </div>
</template>

<script>
import axios from 'axios'
import NavBar from './components/NavBar'

export default {
  name: 'App',
  components: {
    NavBar
  },
  data () {
    return {
      articles: []
    }
  },
  methods: {
    async fetchArticles() {
      let config = {
        headers: {
          'Accept': 'application/json'
        }
      }
      try {
        const articles = await axios.get('https://techcrunch.com/wp-json/wp/v2/posts', config)
        return articles.data
      } catch (err) {
        console.log(err)
      }
    }
  },
  async created() {
    this.articles = await this.fetchArticles()
  }
}
</script>

<style lang="scss">
@font-face {
  font-family: SFProText;
  src: url(./assets/FontsFree-Net-SFProText-Regular.ttf);
}

@font-face {
  font-family: SFProDisplay;
  src: url(./assets/FontsFree-Net-SFProDisplay-Regular.ttf);
}

body {
  margin: 0;
  padding: 0;
  font-family: SFProText;
}

p {
  color: #6E6E6E;
}

h1,h2,h3,h4,h5,h6 {
  color: #2C2C2C;
  font-family: SFProDisplay;
}

h3 {
  font-size: 18px;
}

#container {
  padding-left: 156px;
  padding-right: 156px;
  padding-bottom: 227px;

  @media (max-width: 768px) {
    padding: 0 10px 50px 10px;
  }
}
</style>
