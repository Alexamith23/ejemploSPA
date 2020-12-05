<template>
  <div class="columns">
    <div class="column is-one-third"
    v-for="(post, title) in posts"
    v-bind:key="post.id">
      <app-post :link="post.link">
        <h3 slot="title">{{ post.title }}</h3>
        <span slot="content">{{ post.content }}</span>
      </app-post>
    </div>
  </div>
</template>


<script>
  import Post from './Post.vue'
  export default {
    components: {
      'app-post': Post
    },
    data () {
      return {
        id: this.$route.params.id,
        postsFrontEnd: [
          { id: 1, title: 'Hotel Fortuna', content: 'Un hotel hubicado 75 mts al sur del parque de la Fortuna de San Carlos. 4 estrellas', link: '' }
        ],
        postsMobile: [
          { id: 4, title: 'Hotel Fortuna', content: 'Un hotel hubicado 75 mts al sur del parque de la Fortuna de San Carlos. 4 estrellas', link: '' },
          { id: 5, title: 'Hotel Ciudad Quesada', content: 'Un hotel con vista al volcán arenal, incluye desayuno y almuerzo cada día', link: '' },
          { id: 6, title: 'Hotel Lomas del volcán', content: 'Está ubicado en las faldas del volcán arenal, aguas termales y un hermoso paisaje te esperan', link: '' },
          { id: 7, title: 'Hotel Fortuna', content: 'Un hotel hubicado 75 mts al sur del parque de la Fortuna de San Carlos. 4 estrellas', link: '' },
          { id: 8, title: 'Hotel Ciudad Quesada', content: 'Un hotel con vista al volcán arenal, incluye desayuno y almuerzo cada día', link: '' },
          { id: 9, title: 'Hotel Lomas del volcán', content: 'Está ubicado en las faldas del volcán arenal, aguas termales y un hermoso paisaje te esperan', link: '' }
        ],
        posts: []
      }
    },
    methods: {
      loadPosts () {
        if (this.id === 'front-end') {
          this.posts = this.postsFrontEnd
        } else {
          this.posts = this.postsMobile
        }
      }
    },
    watch: {
      '$route' (to, from) {
        this.id = to.params.id
        this.loadPosts()
      }
    },
    created () {
      this.loadPosts()
      console.log(this.$route.query.page)
    }
  }
</script>
