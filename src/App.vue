<template>
  <div id="app">
    <h1>Новости</h1>
    <NewsList v-bind:listData="listData"/>
  </div>
</template>

<script>

import NewsList from "@/components/NewsList";
export default {
  name: 'App',
  components: {
    NewsList

  },
  data(){
    return {
      listData: [
        {header: "Новость 1", href: "some_href_1", image: "some_image", text: "text about something", rating:"5"},
        {header: "Новость 2", href: "some_href_2", image: "", text: "text about something", rating:"7"},
        {header: "Новость 3", href: "some_href_3", image: "some_image", text: "text about something", rating:"9"},
        {header: "Новость 4", href: "some_href_4", image: "some_image", text: "text about something", rating:"4"},
        {header: "Новость 5", href: "some_href_5", image: "some_image", text: "text about something", rating:"10"},
        {header: "Новость 6", href: "some_href_6", image: "", text: "text about something", rating:"2"},
        {header: "Новость 7", href: "some_href_7", image: "some_image", text: "text about something", rating:"5"},
        {header: "Новость 8", href: "some_href_8", image: "some_image", text: "text about something", rating:"5"},
        {header: "Новость 9", href: "some_href_9", image: "some_image", text: "text about something", rating:"8"},
        {header: "Новость 10", href: "some_href_10", image: "", text: "text about something", rating:"5"},
        {header: "Новость 11", href: "some_href_11", image: "", text: "text about something", rating:"3"},
        {header: "Новость 12", href: "some_href_12", image: "some_image", text: "text about something", rating:"9"},
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
