<template>
    <section class="comments_area">
        <div class="comments_list">
            <ul>
            <li v-for="(comment, index) in comments" :key="index" class="comment_box">
                <div v-if="you(comment)">
                    <img class="comment_icon_me" :src="'./src/images/'+ comment.icon" :alt="comment.username">
                    <p class="comment_text_me" v-text="comment.text"></p>
                </div>
                <div v-else>
                    <img class="comment_icon" :src="'./src/images/'+ comment.icon" :alt="comment.username">
                    <p class="comment_text" v-text="comment.text"></p>
                </div>
            </li>
            </ul>
        </div>

        <div class="comment_add">
          <input class="comment_input" type="text" name="comment" v-model="newComment">
          <button class="comment_add_btn" type="button" name="comment_button" @click="addComment">送信</button>
        </div>

    </section>
</template>

<script>

export default {
    data(){
        return {
            newComment: ""
        }
    },
    props: ["comments","my_account"],
    methods: {
        you(comment){
            return (this.my_account.id == comment.id)
        },
        addComment() {
        this.comments.push({
            id: this.my_account.id,
            username: this.my_account.name,
            icon: this.my_account.icon,
            text: this.newComment
            })
        this.newComment="";
        }
    }
}
</script>

<style>
.comments_area {
  padding: 0 30px;
  height: auto;
  background: var(--comment-bg-color);
  font-size: 1rem;
}
.comments_list {
    width: 440px;
    height: 600px;
    overflow-x: hidden;
    overflow-y: hidden;
}
.comments_list ul {
    width: 440px;
    height:600px;
    padding-right: 17px;
    overflow-x: hidden;
    overflow-y: scroll;
}
.comment_box {
    position: relative;
    display: block;
    width: 440px;
    margin: 20px 0;
    text-align: left;
    min-height: 40px;
    color: white;
}
.comment_box:first-child{
    margin-top: 40px;
}
.comment_icon{
    position: absolute;
    top: 0;
    left: 5px;
    display: block;
    width: 40px;
    height: 40px;
    border-radius: 100%;
}
.comment_text{
    display: block;
    width: 385px;
    margin-left: 55px; 
    padding: 10px 0;
    word-wrap: break-word;
}
.comment_icon_me {
    position: absolute;
    top: 0;
    right: 5px;
    display: block;
    width: 40px;
    height: 40px;
    border-radius: 100%;
}
.comment_text_me {
    display: block;
    width: 330px;
    margin: 0 55px; 
    padding: 10px 0;
    word-wrap: break-word;
}

.comment_add {
    padding: 20px 0;
    font-size:0;
}
.comment_input {
    display: inline-block;
    padding: 5px 0;
    padding-left: 10px;
    width: 380px;
    height: 20px;
    font-size: 0.9rem;
    background: white;
    border-style: none;
}
.comment_add_btn {
    display: inline-block;
    padding: 5px 0;
    width: 50px;
    height: 30px;
    border-style: none;
    font-size: 0.9rem;
    background: var(--comment-btn);
    color: white;
}
</style>
