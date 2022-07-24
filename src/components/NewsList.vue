<template>
  <div>
    <ul>
      <NewsArticle
          v-for="article in paginatedData"
          v-bind:article="article"
          :key="article"
      />
    </ul>
    <button
        :disabled="pageNumber === 0"
        @click="prevPage">
      Previous
    </button>
    <button
        :disabled="pageNumber >= pageCount -1"
        @click="nextPage">
      Next
    </button>
    <div>
      <button @click="changePaginationSize3">
        3
      </button>
      <button @click="changePaginationSize6">
        6
      </button>
      <button @click="changePaginationSize9">
        9
      </button>
    </div>
  </div>
</template>

<script>
import NewsArticle from "@/components/NewsArticle";
export default {
  name: "NewsList",
  components: {NewsArticle},
  data(){
    return {
      pageNumber: 0
    }
  },
  props:{
    listData: {
      type:Array,
      required:true
    },
    size:{
      type:Number,
      required:false,
      default: 6
    }
  },
  created () {
    window.addEventListener('scroll', this.handleScroll);
  },
  unmounted () {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods:{
    nextPage(){
      this.pageNumber++;
    },
    prevPage(){
      this.pageNumber--;
    },
    handleScroll () {

      if((window.innerHeight + window.pageYOffset) >= document.body.offsetHeight && !(this.pageNumber >= this.pageCount -1)){
        this.nextPage();
        window.scrollTo(0,10);
      }
      if(window.innerHeight == window.innerHeight + window.pageYOffset && !(this.pageNumber === 0)) {
        this.prevPage();
      }
      console.log('scroll', window.innerHeight + window.pageYOffset);
      console.log('document.body.offsetHeight', document.body.offsetHeight);
    }
  },
  computed: {
    pageCount() {
      let l = this.listData.length,
          s = this.size;
      return Math.ceil(l / s);
    },
    paginatedData() {
      const start = this.pageNumber * this.size,
          end = start + this.size;
      return this.listData.slice(start, end);
    }
  },
}
</script>

<style scoped>
  ul{
    list-style: none;
  }
  button{
    width:100px;
    height:40px;
    background-color:#eef;
  }

  button:hover{
    cursor:pointer;
  }
  button:hover:disabled{
    cursor:not-allowed;
  }
</style>