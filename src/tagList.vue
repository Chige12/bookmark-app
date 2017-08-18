<template>
      <div class="tag_list">
        <ul>
          <li class="tag_list_item" :class="{active: isActive(tag)}" v-for="tag in tags" :key="tag.id"><a @click="tagSwitching(tag)">{{tag}}</a></li>
        </ul>
    </div>
</template>

<script>

export default {
  data(){
        return {
        }
    },
    props:["tags"],
    methods: {
      isActive(tag) {
        if(this.$parent.active_tag == tag){
            return true;
          }
          else {
            return false;
          }
      },
      tagSwitching(tag) {
          if(this.$parent.active_tag == tag){
            this.$parent.active_tag = null;
          }
          else {
            this.$parent.active_tag = tag;
        }
      }
      
    }
}
</script>

<style>
.tag_list {
  position: fixed;
  top: 0;
  left: 500px;
  margin: 0;
  padding: 10px 0;
  width: 100%;
  background: var(--taglist-bg);
  text-align: left;
}
.tag_list_item:first-child {
  margin-left: 20px; 
}
.tag_list_item {
  display: inline-block;
  background: var(--taglist-bg);
  min-width: 65px;
  border-radius: 13px;
  margin: 0 5px;
}
.tag_list_item a{
    display:block;
    padding: 3px 13px;
    font-size: 0.9rem;
    color: var(--main-bg-color);
    text-align: center;
}
.active {
  background: var(--main-bg-color);
}
.active a {
  color: white;
}
</style>
