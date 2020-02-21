<template>
  <div class="w-2/5">
    <div class="mb-8" v-for="(item, key) in formCount" :key="key">
      <div class="md:flex md:items-center mb-2">
        <div class="md:w-1/4">
          <label class="block text-gray-800 font-bold md:text-right mb-1 md:mb-0 pr-4">
            Link Gambar<sup class="text-red-600 font-bold text-sm">*</sup>
          </label>
        </div>
        <div class="md:w-3/4">
          <input class="inputUrl appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" type="text" name="url" required ref="url">
        </div>
      </div>
      <div class="md:flex md:items-center mb-2">
        <div class="md:w-1/4">
          <label class="block text-gray-800 font-bold md:text-right mb-1 md:mb-0 pr-4">
            Judul Gambar
          </label>
        </div>
        <div class="md:w-3/4">
          <input class="inputTitle appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" type="text" name="title" ref="title">
        </div>
      </div>
      <div class="md:flex md:items-center mb-2">
        <div class="md:w-1/4">
          <label class="block text-gray-800 font-bold md:text-right mb-1 md:mb-0 pr-4">
            Caption Gambar
          </label>
        </div>
        <div class="md:w-3/4">
          <textarea class="inputText form-textarea appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" rows="8" name="text" ref="caption"></textarea>
        </div>
      </div>
    </div>
    <div class="md:flex md:items-center mb-8">
      <div class="md:w-1/4"></div>
      <div class="md:w-3/4">
        <div class="bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded inline-flex items-center" @click="createGallery()">
          <span>Create Gallery</span>
        </div>
        <div class="inline-flex float-right">
          <div class="bg-gray-300 hover:bg-gray-400 text-gray-800 text-white font-bold py-2 px-4 mr-2 text-base rounded-sm" v-if="formCount>1" @click="formCount--;">
            -
          </div>
          <div class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 text-base rounded-sm" @click="formCount++;">
            +
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data(){
    return {
			formCount: 1,
			data: [],
    }
  },
  methods:{
		getInput(){
      this.data = [];
			for(var i=0;i<this.formCount;i++){
        var temp = { "link": this.$refs.url[i].value, "title": this.$refs.title[i].value, "caption": this.$refs.caption[i].value }
				this.data.push(temp);
			}
		},
    createGallery(){
      this.getInput();
      console.log(this.data);
      this.$emit('passData', this.data);
    }
  }
}
</script>