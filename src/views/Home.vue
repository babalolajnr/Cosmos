<template>
  <div>
    <header role="banner">
      <div class="top-bar">
        <div class="container">
          <div class="row">
            <div class="col-9 social">
              <a href="#">
                <span class="fa fa-twitter"></span>
              </a>
              <a href="#">
                <span class="fa fa-facebook"></span>
              </a>
              <a href="#">
                <span class="fa fa-instagram"></span>
              </a>
              <a href="#">
                <span class="fa fa-youtube-play"></span>
              </a>
              <a href="#">
                <span class="fa fa-vimeo"></span>
              </a>
              <a href="#">
                <span class="fa fa-snapchat"></span>
              </a>
            </div>
            <div class="col-3 search-top">
              <!-- <a href="#"><span class="fa fa-search"></span></a> -->
              <form action="#" class="search-top-form">
                <span class="icon fa fa-search"></span>
                <input type="text" id="s" placeholder="Type keyword to search..." />
              </form>
            </div>
          </div>
        </div>
      </div>

      <div class="container logo-wrap">
        <div class="row pt-5">
          <div class="col-12 text-center">
            <a
              class="absolute-toggle d-block d-md-none"
              data-toggle="collapse"
              href="#navbarMenu"
              role="button"
              aria-expanded="false"
              aria-controls="navbarMenu"
            >
              <span class="burger-lines"></span>
            </a>
            <h1 class="site-logo">
              <a href="index.html">Cosmos</a>
            </h1>
          </div>
        </div>
      </div>

      <nav class="navbar navbar-expand-md navbar-light bg-light">
        <div class="container">
          <div class="collapse navbar-collapse" id="navbarMenu">
            <ul class="navbar-nav mx-auto">
              <li class="nav-item">
                <a class="nav-link active" href="index.html">Home</a>
              </li>
              <li class="nav-item dropdown">
                <a
                  class="nav-link dropdown-toggle"
                  href="category.html"
                  id="dropdown04"
                  data-toggle="dropdown"
                  aria-haspopup="true"
                  aria-expanded="false"
                >Travel</a>
                <div class="dropdown-menu" aria-labelledby="dropdown04">
                  <a class="dropdown-item" href="category.html">Asia</a>
                  <a class="dropdown-item" href="category.html">Europe</a>
                  <a class="dropdown-item" href="category.html">Dubai</a>
                  <a class="dropdown-item" href="category.html">Africa</a>
                  <a class="dropdown-item" href="category.html">South America</a>
                </div>
              </li>

              <li
                class="nav-item dropdown"
                @mouseenter="toggleDropdown"
                @mouseleave="toggleDropdown"
                :class="[categoryHover ? 'show' : '' ]"
              >
                <a
                  class="nav-link dropdown-toggle"
                  href="category.html"
                  id="dropdown05"
                  data-toggle="dropdown"
                  aria-haspopup="true"
                  :aria-expanded="[categoryHover ? 'true' : 'false' ]"
                >Categories</a>
                <div
                  :class="[categoryHover ? 'show' : '' ]"
                  class="dropdown-menu"
                  aria-labelledby="dropdown05"
                >
                  <a class="dropdown-item" href="category.html">Lifestyle</a>
                  <a class="dropdown-item" href="category.html">Food</a>
                  <a class="dropdown-item" href="category.html">Adventure</a>
                  <a class="dropdown-item" href="category.html">Travel</a>
                  <a class="dropdown-item" href="category.html">Business</a>
                </div>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="about.html">About</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="contact.html">Contact</a>
              </li>
            </ul>
          </div>
        </div>
      </nav>
    </header>
    <!-- END header -->

    <section class="site-section pt-5">
      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <MyCarousel />
          </div>
        </div>
        <div class="row">
          <div class="col-md-6 col-lg-4" v-for="post in topLatestPosts" :key="post.id">
            <span
              @click="singlePost(post)"
              class="a-block d-flex align-items-center height-md"
              :style="{ backgroundImage: 'url(' + 'http://127.0.0.1:8000/' + `${post.image}` +')'}"
            >
              <div class="text">
                <div class="post-meta">
                  <span class="category">{{ post.category.name }}</span>
                  <span class="mr-2">{{ post.published_at | moment("from", "now") }}</span> &bullet;
                  <span class="ml-2">
                    <span class="fa fa-comments"></span> 3
                  </span>
                </div>
                <h3>{{ post.title }}</h3>
              </div>
            </span>
          </div>
          
        </div>
      </div>
    </section>
    <!-- END section -->

    <section class="site-section py-sm">
      <div class="container">
        <div class="row">
          <div class="col-md-6">
            <h2 class="mb-4">Other Posts</h2>
          </div>
        </div>
        <div class="row blog-entries">
          <div class="col-md-12 col-lg-8 main-content">
            <LatestPosts />
          </div>

          <!-- END main-content -->

          <div class="col-md-12 col-lg-4 sidebar">
            <Sidebar />
          </div>
          <!-- END sidebar -->
        </div>
      </div>
    </section>
    <Footer/>
    
    <!-- END footer -->
  </div>
</template>

<script>
// @ is an alias to /src
import MyCarousel from "@/components/Carousel.vue";
import LatestPosts from "@/components/LatestPosts.vue";
import Sidebar from "@/components/Sidebar.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: {
    MyCarousel,
    LatestPosts,
    Sidebar,
    Footer
  },
  data() {
    return {
      categoryHover: false,
      topLatestPosts: null,
    };
  },
  methods: {
    toggleDropdown: function () {
      if (this.categoryHover === false) {
        this.categoryHover = true;
      } else if (this.categoryHover === true) {
        this.categoryHover = false;
      }
    },
    getTopLatestPosts() {
      this.axios
        .get("http://127.0.0.1:8000/api/topLatestPosts")
        .then((response) => {
          this.topLatestPosts = response.data;
          // console.log(this.topLatestPosts)
        });
    },
    singlePost(post){
      this.$router.push({
        name: 'SinglePost',
        params: {
          slug: post.slug
        }
      })
    }
  },
  mounted() {
    this.getTopLatestPosts();
  },
};
</script>