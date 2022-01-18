<template>
  <div class="container mx-auto p-6 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 bg-gray-100 min-w-full min-h-screen justify-center">

    <div v-for="item in prodData" :key="item.id" :id="item.id" class="col-span-1 flex flex-col bg-white border-2 p-6 w-90 h-120 rounded-xl items-stretch h-full transform transition-all hover:-translate-y-2 duration-300 shadow-lg hover:shadow-2xl items-stretch h-full">

      <img class="h-60 object-cover rounded-xl object-cover rounded-xl" :src="item.image2" alt="">

      <div class="p-2">
        <h2 class="font-bold text-lg mb-2 ">{{ item.name }}</h2>
        <p class="text-sm text-gray-600 text-justify">{{ item.details }}</p>

      </div>
      <div class="flex flex-wrap mt-auto p-2 font-semibold text-sm">
        
      <p class="mr-2 mb-2">Price: {{ item.prices.price.price }} $</p>
    </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Cards',
  props: {},

  data() {
    return { 
      prodData: null
    }
  },
  async created() {
    const response = await axios.get('https://dev.menu.ninja/api/menu/156?key=8j5vfe%24*pfb**rzt&pretty=1')
      this.prodData = response.data.menu.items
    }
}
</script>