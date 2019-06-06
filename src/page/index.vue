<template>
<div >
<Header></Header>
<img src="static/image/test.jpg" alt="刘亦菲">
<div class="article_list">
<ul>
       <li v-for="i in list">
          <time v-text="$utils.goodTime(i.create_at)"></time>
          <router-link :to="'/content/' + i.id">
            {{ i.title }}
          </router-link>
        </li>
</ul>
</div>
<Footer></Footer>
</div>
</template>

<script>
import Header from '../components/header.vue'
import Footer from '../components/footer.vue'
export default {
  components: { Header, Footer },
  data () {
    return {
      list: [1,2,3]
    }
  },
  created () {
    this.getData()
  },
  methods: {
    getData () {
      this.$api.get('topics', {aa:11}, r => {
        this.list=r.data;
      })
    }
  }
}
</script>

<style>
 	 .article_list {margin: auto;}
</style>