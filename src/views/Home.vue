<template>
  <div class="home-page">
    <div class="banner">
      <div class="container">
        <h1 class="logo-font">程序员社区</h1>
        <p>专注于分享知识</p>
      </div>
    </div>
    <div class="container page">
      <div class="row">
        <div class="col-md-12">
          <div class="feed-toggle">
            <ul class="nav nav-pills outline-active">
              <li v-if="isAuthenticated" class="nav-item">
                <router-link
                  :to="{ name: 'home-my-feed' }"
                  class="nav-link"
                  active-class="active"
                >
                  我的文章
                </router-link>
              </li>
              <li class="nav-item">
                <router-link
                  :to="{ name: 'home' }"
                  exact
                  class="nav-link"
                  active-class="active"
                >
                  所有文章
                </router-link>
              </li>
              <li class="nav-item" v-if="tag">
                <router-link
                  :to="{ name: 'home-tag', params: { tag } }"
                  class="nav-link"
                  active-class="active"
                >
                  <i class="ion-pound"></i> {{ tag }}
                </router-link>
              </li>
            </ul>
          </div>
          <router-view></router-view>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import RwvTag from "@/components/VTag";
import { FETCH_TAGS } from "@/store/actions.type";

export default {
  name: "home",
  components: {
    RwvTag
  },
  mounted() {
    this.$store.dispatch(FETCH_TAGS);
  },
  computed: {
    ...mapGetters(["isAuthenticated", "tags"]),
    tag() {
      return this.$route.params.tag;
    }
  }
};
</script>
