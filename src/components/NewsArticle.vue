<template>
  <li>
    <h2>
      <a href="{{ article.href }}">
        {{ article.header }}
      </a>
    </h2>
    <h4>
      рейтинг:
      <select @change="onChange" v-bind:class="{ up: isUp, down:isDown }" v-model="selected">
        <option v-for="option in options" v-bind:value="option" :key="option"
                v-bind:selected="option == article.rating">
          {{ option }}
        </option>
      </select>

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
  props: {
    article: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      options: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
      isUp: false,
      isDown: false,
      selected: this.article.rating
    }
  },
  methods: {
    onChange() {
      if (this.article.rating < this.selected) {
        this.isUp = true;
        this.isDown = false;
      } else {
        this.isUp = false;
        this.isDown = true;
      }
    }
  }
}
</script>

<style scoped>
li {
  border: solid 2px black;
  margin-bottom: 1rem;
  display: flex;
  flex-direction: column;
}

.article_content {
  display: flex;
  justify-content: space-evenly;
}

.up {
  border: solid 2px green;
  background-color: lightgreen;
}

.down {
  border: solid 2px red;
  background-color: salmon;
}
</style>