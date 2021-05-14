<template>
  <div class="hello">
   <VueRssFeed :feedUrl="feedUrl" :name="name" :limit="limit"/>
  </div>
</template>

<script>
import VueRssFeed from "../../node_modules/vue-rss-feed"


export default {
  
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    VueRssFeed
  },
  data() {
    return {
      feedUrl: "https://www.esan.edu.pe/conexion/atom.xml",
      name: "",
      limit: 5,
    };
  },
}
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
