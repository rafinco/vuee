<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tab">
      <div class="tab-item"><router-link to="/goods">商品</router-link></div>
      <div class="tab-item"><router-link to="/ratings">评论</router-link></div>
      <div class="tab-item"><router-link to="/seller">商家</router-link></div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
  import header from './components/header/header.vue';

  const ERR_OK = 0;

  export default {
    data(){
      return {
        seller:{}
      }
    },
    created(){
      this.$http.get('/api/seller').then((response)=>{
        response = response.body;
        if(response.errno===ERR_OK){
          this.seller = response.data;
        }
      })
    },
    components:{
      'v-header':header
    }
  }
</script>

<style>
  .tab{
    display: flex;
    width: 100%;
    height: 40px;
    line-height: 40px;
  }
  .tab .tab-item{
    flex: 1;
    text-align: center
  }
  .tab-item a{
    text-decoration: none;
    display: block;
    font-size: 14px;
    color: #ddd
  }
  .tab-item a.router-link-active{
    color: red;
  }
</style>
