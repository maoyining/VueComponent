<template>
<div>
  <neighbor-switch class="wrapper"
    :data="imageList"
    v-model="currentIndex"
    :loading="loading"
    :loadingText="loadingText"
    :disabled="disabled"
  >
    <!-- 自定义的button -->
    <template v-slot:prev="scoped">
      <button :disabled="scoped.disabled">
        <div class="self-button">&lt;</div>
        </button>
    </template>

    <!-- 自定义的图片列表内容content -->
    <template v-slot:content="scoped">
      <img :src="scoped.item.url"/>
    </template>

    <!-- 自定义的button -->
    <template v-slot:next="scoped">
      <button :disabled="scoped.disabled">&gt;</button>
    </template>
  </neighbor-switch>
</div>
</template>

<script>
import NeighborSwitch from './NeighborSwitch'
export default {
  name: 'Index',
  components: {
    NeighborSwitch: NeighborSwitch,
  },
  data() {
    return {
      currentIndex:0,
      imageList: [{
        url:'./p1.jpg'
      },{
        url:'./p2.jpg'
      },{
        url:'./p3.jpg'
      },{
        url:'./p4.jpg'
      }],
      loadingText:'加载中^_^...',
      loading:false,
      disabled:false
    }
  }
}
</script>
<style scoped>
  .wrapper{
    width:1000px;
    height:600px;
  }
  .self-button{
    border-radius: 50%;
    width:50px;
    height:50px;
    line-height:50px;
    border:0;
    font-size:25px;
    color:#ccc;
    background: #eee;
  }
</style>>



