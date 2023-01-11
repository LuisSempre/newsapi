<template>
  <div class="newslist">
    <div class="container">
      <ul class="media-list">
        <li class="media" v-for="everything in everythings">
          <div class="media-left">
            <a v-bind-href="everything.url" target="_blank">
              <img class="media-object" v-bind:src="everything.urlToImage" />
            </a>
          </div>
          <div class="media-body">
            <h4 class="media-heading">
              <a v-bind:href="everything.url" target="_blank">{{
                everything.title
              }}</a>
            </h4>
            <h5>
              <i>by {{ everything.author }}</i>
            </h5>
            <p>{{ everything.description }}</p>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "newslist",
  props: ["source"],
  data() {
    return {
      everything: [],
    };
  },
  methods: {
    updateSource: function (source) {
      axios
        .get(
          "https://newsapi.org/v2/everything?source=" +
            source +
            "&apiKey=ac05108405a8459fbcf735c9086c5194"
        )
        .then((response) => {
          this.everything = response.data.everything;
        });
    },
  },
  created: function () {
    this.updateSource(this.source);
  },
  watch: {
    source: function (val) {
      this.updateSource(val);
    },
  },
};
</script>

<style scoped>
.media-object {
  width: 128px;
  padding: 10px;
}
.media {
  border-top: 1px solid lightgrey;
  padding-top: 20px;
}
</style>


      <!-- axios
        .get(
          "https://newsapi.org/v2/top-headlines/sources?country=brapiKey=" +
            source +
            "&apiKey=ac05108405a8459fbcf735c9086c5194"
        ) -->
