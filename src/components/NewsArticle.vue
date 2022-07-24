<template>
  <li>
    <h2>
      <a href="{{ article.href }}">
        {{ article.header }}
      </a>
    </h2>
    <h4>
      рейтинг:
      {{ article.rating }}
    </h4>
    <div class="article_content">
      <img v-if="article.image" src="{{ article.image }}">
      <span>
      {{ article.text }}
    </span>
    </div>

  </li>
</template>

<script>
export default {
  name: "NewsArticle",
  props:{
    article:{
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
  li{
    border: solid 2px black;
    margin-bottom: 1rem;
    display: flex;
    flex-direction: column;
  }
  .article_content{
    display: flex;
    justify-content: space-evenly;
  }
</style>