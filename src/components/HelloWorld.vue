<template>
  <div>
      <ul>
        <li v-for="n in list">
          <router-link :to="{name : 'news' ,params:{id : n.id}}">{{n.title}}</router-link>
        </li>
      </ul>
  </div>
</template>

<script type="text/ecmascript-6">
  import Vue from 'vue'
  import VueResource from 'vue-resource'
  Vue.use(VueResource)
  Vue.http.options.emulateJSON = true
export default {
  name: 'HelloWorld',
  data: function() {
    return {
      list: ''
    }
  },
  mounted : function(){
    this.getList();
  },
  methods: {
    getList: function(){
      this.$http({
        url: 'http://localhost:3000/test1',
        method: 'GET',
        headers: {
          'Content-Type': 'x-www-from-urlencoded'
        }
      }).then((response)=>{
        console.log(response);
        this.list = response.data;
      });
    }
  }
}
</script>

<style scoped>

</style>
