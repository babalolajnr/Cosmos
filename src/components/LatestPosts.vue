<template>
  <div>
    <div class="row">
      <div class="col-md-6" v-for="post in posts" :key="post.id">
        <span
          @click="singlePost(post)"
          class="blog-entry element-animate fadeIn element-animated"
          data-animate-effect="fadeIn"
        >
          <img :src="'http://127.0.0.1:8000/' + post.image" :alt="post.title" />
          <div class="blog-content-body">
            <div class="post-meta">
              <span class="category">{{ post.category.name }}</span>
              <span class="mr-2">{{ post.published_at | moment("from", "now") }}</span> •
              <span class="ml-2">
                <span class="fa fa-comments"></span> 3
              </span>
            </div>
            <h2>{{ post.title }}</h2>
          </div>
        </span>
      </div>
    </div>

    <div class="row">
      <div class="col-md-12 text-center">
        <nav aria-label="Page navigation" class="text-center">
          <ul class="pagination">
            <li class="page-item active">
              <a class="page-link" href="#">Prev</a>
            </li>
            <li class="page-item">
              <a class="page-link" href="#">1</a>
            </li>
            <li class="page-item">
              <a class="page-link" href="#">2</a>
            </li>
            <li class="page-item">
              <a class="page-link" href="#">3</a>
            </li>
            <li class="page-item">
              <a class="page-link" href="#">Next</a>
            </li>
          </ul>
        </nav>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "LatestPosts",
  data() {
    return {
      posts: null,
      
      ctx: {
        currentPage: null,
        firstPageUrl: null,
        from: null,
        lastPage: null,
        lastPageUrl: null,
        nextPageUrl: null,
        path: null,
        perPage: null,
        prevPageUrl: null,
        to: null,
        total: null,
      },
    };
  },
  methods: {
    getLatestPosts() {
      this.axios
        .get("http://127.0.0.1:8000/api/latestPosts")
        .then((response) => {
          this.posts = response.data[0].data;

          this.ctx.currentPage = response.data[0].current_page;
          this.ctx.firstPageUrl = response.data[0].first_page_url;
          this.ctx.from = response.data[0].from;
          this.ctx.lastPage = response.data[0].last_page;
          this.ctx.lastPageUrl = response.data[0].last_page_url;
          this.ctx.nextPageUrl = response.data[0].next_page_url;
          this.ctx.path = response.data[0].path;
          this.ctx.perPage = response.data[0].per_page;
          this.ctx.prevPageUrl = response.data[0].prev_page_url;
          this.ctx.to = response.data[0].to;
          this.ctx.total = response.data[0].total;

          this.posts = this.posts.slice(3, 11)
          
          
        }).catch((err)=>{
          console.log(err)
        });
    },
   
    singlePost(post) {
      this.$router.push({
        name: "SinglePost",
        params: {
          slug: post.slug,
        },
      });
    },
  },
  mounted() {
    this.getLatestPosts();
  },
};
</script>

<style>
</style>