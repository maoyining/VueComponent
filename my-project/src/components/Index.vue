<template>
<div>
  <neighbor-switch
    :data="imageList"
    v-model="currentIndex"
  >
    <template v-slot:content="scoped">
      <img :src="scoped.attribute.url"/>
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
      }]
    }
  }
}
</script>

<style scoped>

</style>