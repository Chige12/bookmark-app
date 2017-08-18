<template>
  <nav class="left_side">

      <header class="book_top">
        <img class="book_top_icon" :src="'./src/images/'+ work_link.icon">
        <h1 class="book_top_title">{{this.work_link.name}}</h1>
        <p class="book_top_master">master: <span>{{work_link.master}}</span></p>
      </header>

      <comments-area :comments="comments" :my_account="my_account"></comments-area>
      <share-url :work_link="work_link"></share-url>

    </nav>
</template>

<script>
import CommentsArea from "./commentsArea.vue"
import ShareUrl from "./shareUrl.vue"

export default {
  props: ["comments","work_link","my_account"],//userのデータも持ってくる
  data(){
    return {
    }
  },
  components:{
    "comments-area":CommentsArea,
    "share-url":ShareUrl
  },

}

</script>

<style>
.left_side {
  position: fixed;
  top: 0;
  left: 0;
  margin: 0;
  width: 500px;
  height: 100%;
  background: var(--main-bg-color);
  text-align: center;
  color: white;
}
.book_top {
  padding: 25px 0;
}
.book_top_icon {
  margin: 0 auto;
  width: 70px;
  height: 70px;
  border-radius: 100%;
}
.book_top_title {
  margin: 0;
  padding-top: 15px;
  font-size: 1.3rem;
}
.book_top_master {
  margin: 0;
  padding-top: 8px;
  font-size: 0.9rem;
}
</style>
