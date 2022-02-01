<template>
  <div id="app">
    <Header :index="this.index" />
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <Content
            v-if="questionlist.length"
            :cQuestion="questionlist[index]"
            :next="next"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Content from "./components/content.vue";
// import ram from "./components/ram.vue";
// import sam from "./components/sam.vue";

export default {
  name: "App",
  components: {
    Header,
    Content,
    // ram,
    // sam,
  },
  data() { 
    return {
      questionlist: [],
      index: 0,
    };
  },
  methods: {
    next(){
      if(this.index<9)
      this.index  ++;
    }
  },
  mounted() {
    fetch("https://opentdb.com/api.php?amount=10", {
      method: "get",
    })
      .then((response) => {
        return response.json();
      })
      .then((result) => {
        this.questionlist = result.results;
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
  margin-top: 60px;
}
</style>
