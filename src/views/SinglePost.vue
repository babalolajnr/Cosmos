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
            <div class="col-3 search-icon">
              <a href="#">
                <span class="fa fa-search"></span>
              </a>
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
            <h1>
              <a href="index.html">Balita</a>
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

              <li class="nav-item dropdown">
                <a
                  class="nav-link dropdown-toggle"
                  href="category.html"
                  id="dropdown05"
                  data-toggle="dropdown"
                  aria-haspopup="true"
                  aria-expanded="false"
                >Categories</a>
                <div class="dropdown-menu" aria-labelledby="dropdown05">
                  <a class="dropdown-item" href="category.html">Lifestyle</a>
                  <a class="dropdown-item" href="category.html">Food</a>
                  <a class="dropdown-item" href="category.html">Adventure</a>
                  <a class="dropdown-item" href="category.html">Travel</a>
                  <a class="dropdown-item" href="category.html">Business</a>
                </div>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="blog.html">Blog</a>
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

    <section class="site-section py-lg">
      <div class="container">
        <div class="row blog-entries">
          <div class="col-md-12 col-lg-8 main-content">
            <h1 class="mb-4">{{ post.title }}</h1>
            <div class="post-meta">
              <span class="category">{{ post.category.name }}</span>
              <span class="mr-2">{{ post.published_at | moment("from", "now") }}</span> &bullet;
              <span class="ml-2">
                <span class="fa fa-comments"></span> 3
              </span>
            </div>
            <div class="post-content-body">
              <div class="row mb-5">
                <div class="col-md-12 mb-4">
                  <img
                    :src="'http://127.0.0.1:8000/' + post.image"
                    alt="Image placeholder"
                    class="img-fluid"
                  />
                </div>
                <p v-html="post.body"></p>
              </div>
             </div>

            <div class="pt-5">
              <p>
                Category:
                <a href="#">{{ post.category.name }}</a>
                 Tags:
                <a v-for="tag in post.tags" :key="tag" href="#">{{ tag }}</a>
              </p>
            </div>

            <div class="pt-5">
              <h3 class="mb-5">6 Comments</h3>
              <ul class="comment-list">
                <li class="comment">
                  <div class="vcard">
                    <img src="images/person_1.jpg" alt="Image placeholder" />
                  </div>
                  <div class="comment-body">
                    <h3>Jean Doe</h3>
                    <div class="meta">January 9, 2018 at 2:21pm</div>
                    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur quidem laborum necessitatibus, ipsam impedit vitae autem, eum officia, fugiat saepe enim sapiente iste iure! Quam voluptas earum impedit necessitatibus, nihil?</p>
                    <p>
                      <a href="#" class="reply">Reply</a>
                    </p>
                  </div>
                </li>

                <li class="comment">
                  <div class="vcard">
                    <img src="images/person_1.jpg" alt="Image placeholder" />
                  </div>
                  <div class="comment-body">
                    <h3>Jean Doe</h3>
                    <div class="meta">January 9, 2018 at 2:21pm</div>
                    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur quidem laborum necessitatibus, ipsam impedit vitae autem, eum officia, fugiat saepe enim sapiente iste iure! Quam voluptas earum impedit necessitatibus, nihil?</p>
                    <p>
                      <a href="#" class="reply">Reply</a>
                    </p>
                  </div>

                  <ul class="children">
                    <li class="comment">
                      <div class="vcard">
                        <img src="images/person_1.jpg" alt="Image placeholder" />
                      </div>
                      <div class="comment-body">
                        <h3>Jean Doe</h3>
                        <div class="meta">January 9, 2018 at 2:21pm</div>
                        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur quidem laborum necessitatibus, ipsam impedit vitae autem, eum officia, fugiat saepe enim sapiente iste iure! Quam voluptas earum impedit necessitatibus, nihil?</p>
                        <p>
                          <a href="#" class="reply">Reply</a>
                        </p>
                      </div>

                      <ul class="children">
                        <li class="comment">
                          <div class="vcard">
                            <img src="images/person_1.jpg" alt="Image placeholder" />
                          </div>
                          <div class="comment-body">
                            <h3>Jean Doe</h3>
                            <div class="meta">January 9, 2018 at 2:21pm</div>
                            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur quidem laborum necessitatibus, ipsam impedit vitae autem, eum officia, fugiat saepe enim sapiente iste iure! Quam voluptas earum impedit necessitatibus, nihil?</p>
                            <p>
                              <a href="#" class="reply">Reply</a>
                            </p>
                          </div>

                          <ul class="children">
                            <li class="comment">
                              <div class="vcard">
                                <img src="images/person_1.jpg" alt="Image placeholder" />
                              </div>
                              <div class="comment-body">
                                <h3>Jean Doe</h3>
                                <div class="meta">January 9, 2018 at 2:21pm</div>
                                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur quidem laborum necessitatibus, ipsam impedit vitae autem, eum officia, fugiat saepe enim sapiente iste iure! Quam voluptas earum impedit necessitatibus, nihil?</p>
                                <p>
                                  <a href="#" class="reply">Reply</a>
                                </p>
                              </div>
                            </li>
                          </ul>
                        </li>
                      </ul>
                    </li>
                  </ul>
                </li>

                <li class="comment">
                  <div class="vcard">
                    <img src="images/person_1.jpg" alt="Image placeholder" />
                  </div>
                  <div class="comment-body">
                    <h3>Jean Doe</h3>
                    <div class="meta">January 9, 2018 at 2:21pm</div>
                    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur quidem laborum necessitatibus, ipsam impedit vitae autem, eum officia, fugiat saepe enim sapiente iste iure! Quam voluptas earum impedit necessitatibus, nihil?</p>
                    <p>
                      <a href="#" class="reply">Reply</a>
                    </p>
                  </div>
                </li>
              </ul>
              <!-- END comment-list -->

              <div class="comment-form-wrap pt-5">
                <h3 class="mb-5">Leave a comment</h3>
                <form action="#" class="p-5 bg-light">
                  <div class="form-group">
                    <label for="name">Name *</label>
                    <input type="text" class="form-control" id="name" />
                  </div>
                  <div class="form-group">
                    <label for="email">Email *</label>
                    <input type="email" class="form-control" id="email" />
                  </div>
                  <div class="form-group">
                    <label for="website">Website</label>
                    <input type="url" class="form-control" id="website" />
                  </div>

                  <div class="form-group">
                    <label for="message">Message</label>
                    <textarea name id="message" cols="30" rows="10" class="form-control"></textarea>
                  </div>
                  <div class="form-group">
                    <input type="submit" value="Post Comment" class="btn btn-primary" />
                  </div>
                </form>
              </div>
            </div>
          </div>

          <!-- END main-content -->

          <div class="col-md-12 col-lg-4 sidebar">
            <Sidebar />
          </div>
          <!-- END sidebar -->
        </div>
      </div>
    </section>

    <section class="py-5">
      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <h2 class="mb-3">Related Post</h2>
          </div>
        </div>
        <div class="row">
          <div class="col-md-6 col-lg-4">
            <a
              href="#"
              class="a-block d-flex align-items-center height-md"
              style="background-image: url('images/img_2.jpg'); "
            >
              <div class="text">
                <div class="post-meta">
                  <span class="category">Lifestyle</span>
                  <span class="mr-2">March 15, 2018</span> &bullet;
                  <span class="ml-2">
                    <span class="fa fa-comments"></span> 3
                  </span>
                </div>
                <h3>There’s a Cool New Way for Men to Wear Socks and Sandals</h3>
              </div>
            </a>
          </div>
          <div class="col-md-6 col-lg-4">
            <a
              href="#"
              class="a-block d-flex align-items-center height-md"
              style="background-image: url('images/img_3.jpg'); "
            >
              <div class="text">
                <div class="post-meta">
                  <span class="category">Travel</span>
                  <span class="mr-2">March 15, 2018</span> &bullet;
                  <span class="ml-2">
                    <span class="fa fa-comments"></span> 3
                  </span>
                </div>
                <h3>There’s a Cool New Way for Men to Wear Socks and Sandals</h3>
              </div>
            </a>
          </div>
          <div class="col-md-6 col-lg-4">
            <a
              href="#"
              class="a-block d-flex align-items-center height-md"
              style="background-image: url('images/img_4.jpg'); "
            >
              <div class="text">
                <div class="post-meta">
                  <span class="category">Food</span>
                  <span class="mr-2">March 15, 2018</span> &bullet;
                  <span class="ml-2">
                    <span class="fa fa-comments"></span> 3
                  </span>
                </div>
                <h3>There’s a Cool New Way for Men to Wear Socks and Sandals</h3>
              </div>
            </a>
          </div>
        </div>
      </div>
    </section>
    <!-- END section -->
    <Footer />
    <!-- END footer -->
  </div>
</template>

<script>
import Sidebar from "@/components/Sidebar.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: {
    Sidebar,
    Footer
  },
  data() {
    return {
      post: null,
    };
  },
  mounted() {
    this.getSinglePost();
  },
  methods: {
    getSinglePost() {
      this.axios
        .get(`http://127.0.0.1:8000/api/singlePost/${this.$route.params.slug}`)
        .then((response) => {
          this.post = response.data;
          // console.log(this.post.title)
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>
