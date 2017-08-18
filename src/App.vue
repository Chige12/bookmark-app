<template>
  <div class="root">
    <left-side :comments="comments" :work_link="work_link" :my_account="my_account"></left-side>

    <main>
      <tag-list :tags="tags"></tag-list>
      <site-list :sites="sites" :active_tag="active_tag"></site-list>
    </main>
    <button class="site_add_btn" type="button">+</button>

  </div>
</template>

<script>

import LeftSide from "./leftSide.vue"
import TagList from "./tagList.vue"
import SiteList from "./siteList.vue"

export default {
  data(){
    return {
      comments: [],
      sites: [],
      tags: [],
      work_link:{
        name:"チームで仕事用のリンク集",
        master: "yasuirisa",
        icon: "bookmark_icon.png",
        share_url: "hogehoge.com",
      },
      my_account: {id:"001", name:"yasuirisa", icon:"YASUI.png"},
      active_tag: null,
    }
  },
  components:{
    "left-side":LeftSide,
    "site-list":SiteList,
    "tag-list":TagList
  },
  mounted(){
    $.get("/api.json").done((res)=>{
      this.tags = res.tags;
      this.sites = res.sites;
      this.comments = res.comments;
    })
  }
}

</script>

<style>
body {
  margin: 0;
  --main-bg-color: #657786;
  --comment-bg-color: rgba(255, 255, 255, 0.15);
  --comment-btn: #AAB8C2;
  --taglist-bg: #E1E8ED;
  --list-bg-color: #F5F8FA;
  
}
.root {
  width: 100%;
  height: 100vh;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  font-size: 65px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 0;
  font-size: 1rem;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0;
}
p {
  margin: 0;
  padding: 0;
}
a {
  color: #42b983;
  text-decoration: none;
  cursor: pointer;
}

main {
  display: block;
  padding-left: 500px;
  padding-top: 40px;
}
.site_add_btn {
  position: fixed;
  bottom: 40px;
  right: 40px;
  width: 60px;
  height: 60px;
  border-radius: 100%;
  border-style: none;
  background: #42b983;
  color: white;
  font-size: 2.3rem;
  text-align: center;
  box-shadow: 2px 2px 10px 0px rgba(0,0,0,0.4);
  -moz-box-shadow: 2px 2px 10px 0px rgba(0,0,0,0.4);
  -webkit-box-shadow: 2px 2px 10px 0px rgba(0,0,0,0.4);
  transition: 0.2s;
}
.site_add_btn:hover {
  box-shadow: 3px 3px 12px 0px rgba(0,0,0,0.6);
  -moz-box-shadow: 3px 3px 12px 0px rgba(0,0,0,0.6);
  -webkit-box-shadow: 3px 3px 12px 0px rgba(0,0,0,0.6);
}
</style>
