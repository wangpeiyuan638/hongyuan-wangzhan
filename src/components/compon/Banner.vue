<template>
  <swiper :options="swiperOption" ref="mySwiper">
    <!-- slides -->
    <swiper-slide v-for="item in imglist">
    	<img :src="rootLink+ '/resources/img/' + item.imgPath"/>
    </swiper-slide>
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
</template>

<script>
	import axios from 'axios'
  export default {
    name: 'carrousel',
    data() {
      return {
      	rootLink: 'http://119.23.28.239:8080',
      	imglist:[],
        swiperOption: {
          autoplay: 3000,
          loop: true,
          pagination : '.swiper-pagination',
          paginationClickable :true
        }
      }
    },
    mounted() {
    	var vm = this;
		axios.get(vm.rootLink + '/train/homePage/banner?type=上面')
		  .then(function (data) {
			vm.imglist =  data.data.data
		})
    }
  }
</script>
<style>
	.swiper-container{
		width: 100%;
		height: 100%;
		overflow: hidden;
	}
	.swiper-wrapper{
		width: 100%;
		height: 100%;
	}
	.swiper-slide{
		width: 100%;
		height: 100%;
	}
	.swiper-container{
		width: 100%;
		height: 100%;
	}
	.swiper-container img{
		width: 100%;
		height: 100%;
	}
</style>