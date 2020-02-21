<template>
  <div class="w-3/5 px-4">
    <div class="full relative">
      <div class="w-full bg-cover" style="padding-bottom: 56.25%;" :style="{ 'background-image': 'url(' + theData[index].link + ')'}"></div>
      <div class="py-2 text-center">
        <h3 class="text-2xl font-bold">{{ theData[index].title }}</h3>
        <p>{{ theData[index].caption }}</p>
      </div>
      <div class="prev" @click="prev()"> Prev </div>
      <div class="next" @click="next()"> Next </div>
    </div>
    <hr>
    <p class="py-4">Thumbs:</p>
    <div class="flex">
      <div class="w-1/4 px-1 text-center" v-for="(data, key) in theData" :key="key" @click="index = key" :class="{ active : key == index }">
        <div class="w-full bg-cover" style="padding-bottom: 56.25%;" :style="{ 'background-image': 'url(' + data.link + ')'}"></div>
        <div class="py-2">
          <p>{{ data.title }}</p>
        </div>
      </div>
    </div>

  </div>
</template>
<script>
export default {
  props:{
    theData: Array,
  },
  data(){
    return{
      index: 0
    }
  },
  methods:{
      prev(){
        if(this.index > 0) this.index--;
      },
      next(){
        if(this.index < this.theData.length-1) this.index++;
      }
  }
}
</script>
<style scoped>
  .active{
    filter: contrast(0.3);
  }
  .prev, .next{
    position: absolute;
    left: 0;
    top: 40%;
    transform: translateY(-50%);
    background: white;
    padding: 10px;
    cursor: pointer;
  }
  .next{
    left: auto;
    right: 0;
  }
</style>