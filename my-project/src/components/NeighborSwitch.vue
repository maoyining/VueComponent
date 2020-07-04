<template>
  <div class="wrapper">
    <div class="wrapper-button">
      <button class="button-left" @click="prev">&lt;</button>
    </div>
    <slot name="content" :attribute="imageList[currentIndex]"></slot>
    <div class="wrapper-button">
      <button class="button-right" @click="next">&gt;</button>
    </div>
  </div>
</template>

<script>
export default {
  name:'NeighborSwitch',
  props:{
    data: Array,
    value: Number
  },
  data(){
    return {
      currentIndex: this.value,
      imageList: this.data
    }
  },
  methods:{
    next(){
      if(this.currentIndex<this.imageList.length-1){
        this.currentIndex++;
      }else{
        this.currentIndex = 0;
      }
    },
    prev(){
      if(this.currentIndex!==0){
        this.currentIndex--;
      }else{
        this.currentIndex = this.imageList.length-1
      }
    }
  }
}
</script>

<style scoped>
.wrapper{
  width:800px;
  height:400px;
  line-height:400px;
  border:solid 1px #eee;
  background-size: contain;
  position: relative;
}
.wrapper img{
  width:600px;
  height:400px;
  vertical-align: top;
}
.wrapper-button{
  line-height:400px;
  display:inline-block;
  width:100px;
  height:100%;
  vertical-align: top;
}
.button-right,.button-left {
  display:inline-block;
  margin:0 auto;
  border-radius: 50%;
  width:50px;
  height:50px;
  border:0;
  font-size:25px;
  color:#ccc;
  outline: none;
  cursor: pointer;
}

</style>