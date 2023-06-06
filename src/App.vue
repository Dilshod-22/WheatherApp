<template>
  <div class="h-screen w-full app flex items-center justify-center">
    <infoItem v-if="info" :info="info" @cancel="cancel"/>
    <searchPlace
      v-bind:infos="infos"
      v-model="search"
      @getInfo="getInfo"
      v-else
    />
  </div>
</template>

<script>
import searchPlace from "./views/searchPlace.vue";
import infoItem from "./views/infoItem.vue";

export default {
  data() {
    return {
      search: "",
      infos: [],
      info: null,
    };
  },
  components: {
    searchPlace,
    infoItem,
  },
  watch: {
    async search() {
      const url = `https://weatherapi-com.p.rapidapi.com/search.json?q=%3C${this.search}%3E`;
      const options = {
        method: "GET",
        headers: {
          "X-RapidAPI-Key":
            "3df7cba90cmsh3cf97b08ac00df2p1ff8cejsn24f3cd5d976d",
          "X-RapidAPI-Host": "weatherapi-com.p.rapidapi.com",
        },
      };

      try {
        const response = await fetch(url, options);
        const result = await response.text();
        let res = JSON.parse(result);
        this.infos = res;
      } catch (error) {
        console.error(error);
      }
    },
  },

  methods: {
    async getInfo(item) {
      const url = `https://weatherapi-com.p.rapidapi.com/forecast.json?q=${item}&days=3`;
      const options = {
        method: "GET",
        headers: {
          "X-RapidAPI-Key":
            "3df7cba90cmsh3cf97b08ac00df2p1ff8cejsn24f3cd5d976d",
          "X-RapidAPI-Host": "weatherapi-com.p.rapidapi.com",
        },
      };

      try {
        const response = await fetch(url, options);
        const result = await response.text();
        let res = JSON.parse(result);
        this.info = res;
        console.log(res);
      } catch (error) {
        console.error(error);
      }
    },
    cancel(){
      this.info=null
      this.infos = ""
    }
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  background-image: url("./assets/128744.webp");
  background-size: cover;
}

.search {
  background: none;
}
</style>
