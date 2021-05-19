<template>
  <div class="hello">
    {{ description }}
    <div>
      <div v-for="item in article">
        <li>{{ item.title }}</li>
        <!-- <li>{{ item.content_html }}</li> -->
        <p>Using v-html directive: <span v-html="item.content_html "></span></p>
      </div>
      
      <!-- <h1> {{ title }} </h1> -->
      <!-- <p>{{ summary }}</p> -->
      <!-- <p> {{url}} </p> -->
    </div>
  </div>
</template>

<script>
import feed2json from "feed2json";
import request from "request";

export default {
  name: "HelloWorld",
  data() {
    return {
      description: "",
      article: [],

      // title:{},
      // url:{},
      // author:{}
    };
  },

  created() {
    let url = "https://www.esan.edu.pe/conexion/atom.xml";
    let req = request(url);

    feed2json.fromStream(req, url, (err, json) => {
      this.description = json.description;
      this.article = json.items;
      console.log(json.items);
      // this.article.forEach(function (obj) {
      //   con
      //  this.summary.push(obj.this.summary);

      // });
      // this.summary=json.items.summary

      // for (let index = 0; index < this.article.length; index++) {
      //   let articles  = this.article[index]
      //   this.summary = articles.summary
      //   this.title=articles.title
      //   this.url = articles.url
      //   this.author=articles.author
      // }
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
