<template>
  <div v-html="newsHtml">
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    name: 'news',
    data: function () {
      return {
        newsHtml: '',
        dataUrl : 'http://localhost:3000/test2/'+ this.$route.params.id
      }
    },
    mounted: function () {
      this.getData();
    },
    methods: {
      getData: function () {
        this.$http({
          url: this.dataUrl,
          method: 'GET',
          headers: {
            'Content-Type': 'x-www-from-urlencoded'
          }
        }).then((response)=>{
          var res = response.data;
          console.log(res);
          this.newsHtml = res[0].content;
        }).catch(function (response) {
          console.log(response)
        })
      }
    }
  }
</script>
