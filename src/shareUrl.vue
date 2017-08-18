<template>
    <section class="share">
        <p class="share_txt">share</p>
        <div class="share_urlbox">
            <div class="share_url" v-text="work_link.share_url"></div>
            <button class="share_btn" type="button" name="url_copy_button" @click="copyUrlBtn">Copy</button>
        </div>
    </section>
</template>

<script>
export default {
    data(){
        return {
        }
    },
    props: ["work_link"],
    methods: {
        copyUrlBtn() {
        execCopy(this.work_link.share_url);
    }
  }
}
function execCopy(string){
  var temp = document.createElement('textarea');
  
  temp.value = string;
  temp.selectionStart = 0;
  temp.selectionEnd = temp.value.length;
  
  var s = temp.style;
  s.position = 'fixed';
  s.left = '-100%';
  
  document.body.appendChild(temp);
  temp.focus();
  var result = document.execCommand('copy');
  temp.blur();
  document.body.removeChild(temp);
  // true なら実行できている falseなら失敗か対応していないか
  return result;
}
</script>

<style>
.share {
    margin: 20px 0;
    padding: 0 30px;
}
.share_txt {
    font-size: 0.9rem;
}
.share_urlbox {
    margin-top: 15px; 
    position: relative;
}
.share_url {
    display: block;
    padding: 5px 0;
    padding-left: 10px;
    text-align: left;
    width: 428px;
    height: 18px;
    font-size: 0.9rem;
    color: white;
    border: 1px solid var(--comment-btn);
}
.share_btn {
    position: absolute;
    display: block;
    top: 0;
    right: 0;
    width: 50px;
    height: 30px;
    border-style: none;
    font-size: 0.9rem;
    background: var(--comment-btn);
    color: white;
}
</style>
