<template>
    <div class="site_list">
        <ul>
          <li v-if="activeTag(site)" v-for="(site, index) in sites" :key="index" class="site_box">
            <img class="site_thumbnail" :src="'./src/images/'+ site.thumbnail" alt=""><!--
         --><div class="site_info">
              <h2 class="site_title" v-text="site.title"></h2>
              <a class="site_url" :href="site.url" v-text="'■ '+ site.url"></a>
              <p class="site_discription" v-text="site.discription"></p>
            </div>
            <div class="site_tag">
              <ul>
                <li class="site_tag_item" v-for="(tag, index) in site.tags" :key="index"><a>{{tag}}</a></li>
              </ul>
            </div>
          </li>
        </ul>
    </div>
</template>

<script>

export default {
  props:["sites","active_tag"],
  methods: {
    activeTag(site){
      for(var i=0; i<=site.tags.length; i++){
        if(this.active_tag == site.tags[i]){
          return true;
        }
      }
      return false;
    }
  }
}

</script>

<style>
.site_list {
  width: 100%;
  height: 100%;
  margin: 0;
  text-align: left;
}

.site_box {
  display: block;
  margin: 20px;
  padding: 10px;
  background: var(--list-bg-color);
  transition: 0.2s;
}

.site_thumbnail {
  display: inline-block;
  width: 120px;
  height: 80px;
}
.site_info {
  padding-left: 20px;
  display: inline-block;
  color: var(--main-bg-color);
  vertical-align: top;
}
.site_title {
  font-size: 1.2rem;
  margin: 3px 0;
}
.site_url {
  font-size: 0.9rem;
}
.site_discription {
    margin: 5px 0;
    font-size: 0.9rem;
}
.site_tag {
  margin: 0;
  width: 100%;
  padding-top: 5px;
}
.site_tag_item {
  display: inline-block;
  background: var(--list-bg-color);
  background: var(--main-bg-color);
  min-width: 50px;
  margin: 0 3px;
  border-radius: 12px;
}
.site_tag_item a{
    display:block;
    padding: 2px 10px;
    font-size: 0.8rem;
    color: white;
    text-align: center;
}
</style>
