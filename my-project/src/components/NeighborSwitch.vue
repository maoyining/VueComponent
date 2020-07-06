<template>
<div class="wrapper">
  <div class="pic-wrapper">
    <div  v-if="loading">
      {{loadingText}}
    </div>
    <div v-else>
      <div class="wrapper-button-left" @click="prev($event)">
        <slot name="prev" :disabled="disabled"></slot>
      </div>
      <slot name="content" :item="imageList[currentIndex]"></slot>
      <div class="wrapper-button-right" @click="next($event)">
        <slot name="next" :disabled="disabled"></slot>
      </div>
    </div>
  </div>
  <div class="current-pic">{{currentIndex+1}}</div>
</div>
</template>

<script>
export default {
  name:'NeighborSwitch',
  props:{
    data: Array,
    value: Number,
    loading: Boolean,
    loadingText: String,
    disabled: Boolean
  },
  data(){
    return {
      currentIndex: this.value,
      imageList: this.data,
    }
  },
  mounted() {
    document.addEventListener('keyup',this.handleKeyUp)
  },
  beforeDestroy(){
    document.removeEventListener('keyup',this.handleKeyUp)
  },
  methods:{
    handleKeyUp(e) {
      if(e.key==='ArrowRight'){
        this.next(e)
      } else if (e.key==='ArrowLeft') {
        this.prev(e)
      }
    },
    next(e){
      if(e.target.nodeName==="BUTTON" || e.key==='ArrowRight'){
        if(this.currentIndex < this.imageList.length-1){
          this.currentIndex++
        }else{
          this.currentIndex = 0
        }
      }
    },
    prev(e){
      if(e.target.nodeName==="BUTTON" || e.key==='ArrowLeft'){
        if(this.currentIndex!==0){
        this.currentIndex--
        }else{
          this.currentIndex = this.imageList.length-1
        }
      }
    }
  }
}
</script>

<style scoped>
.wrapper{
  width:100%;
}
.pic-wrapper{
  width:100%;
  height:100%;
  overflow: hidden;
  border:solid 1px #eee;
  position:relative;
}
.pic-wrapper img{
  width:80%;
  display:block;
  position:absolute;
  left:50%;
  top:50%;
  transform: translate(-50%,-50%);
}
.wrapper-button-left{
  width:10%;
  vertical-align: top;
  float:left;
  position:absolute;
  top:50%;
  transform: translateY(-50%);
}
.wrapper-button-right{
  width:10%;
  vertical-align: top;
  float:right;
  position:absolute;
  left:90%;
  top:50%;
  transform: translateY(-50%);
}
.wrapper-button-left button,.wrapper-button-right button{
  display:inline-block;
  margin:0 auto;
  outline: none;
  cursor: pointer;
}
.current-pic {
  width:40px;
  height:40px;
  border:1px solid #eee;
  border-radius: 50%;
  text-align: center;
  line-height: 40px;
  margin:10px auto;
  color:#ccc
}
</style>