<template>
    <div>
     <div class="banner" @click="handleBannerClick">
        <img
        class="banner-img" 
         :src="bannerImg" alt="">
         <div class="banner-info">
             <div class="banner-title"> {{this.sightName}}</div>
             <div class="banner-number">
                  <span class="iconfont banner-icon">&#xe692;</span>
                    {{this.bannerImgs.length}}</div>
         </div>
        </div>   
        <fade-animation>
              <common-gallary 
              :imgs="bannerImgs" 
              v-show="showGallary"
              @close="handleGallaryClose"
             >
        </common-gallary>
        </fade-animation>
      
    </div> 
</template>

<script>
import CommonGallary from "common/gallery/Gallery";
import FadeAnimation from "common/fade/Fade";
export default {
  name: "DetailBanner",
  props:{
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  data(){
      return{
      showGallary:false,
      imgs:["http://img1.qunarzz.com/sight/p0/1711/fb/fb601f1e71f9d4aba3.img.jpg_r_800x800_92d85f99.jpg",
             "http://img1.qunarzz.com/sight/p0/1711/da/dac7cd5bfa983877a3.img.jpg_r_800x800_7aec58e7.jpg"]
      }
  },
  methods:{
      handleBannerClick(){
          this.showGallary=true
      },
      handleGallaryClose(){
          this.showGallary=false
      }
  },
  components: {
    CommonGallary,
    FadeAnimation
  }
};
</script>

<style lang="stylus" scoped>
.banner {
    position: relative;
    overflow: hidden;
    height: 0;
    padding-bottom: 55%;

    .banner-img {
        width: 100%;
    }

    .banner-info {
        display: flex;
        position: absolute;
        left: 0;
        right: 0;
        bottom: 0;
        line-height: 0.6rem;
        color: #ffffff;
        background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8));

        .banner-title {
            font-size: 0.32rem;
            padding: 0 0.2rem;
            flex: 1;
        }

        .banner-number {
            height: 0.32rem;
            margin-top: 0.14rem;
            padding: 0 0.4rem;
            line-height: 0.32rem;
            border-radius: 0.2rem;
            font-size: 0.24rem;
            background: rgba(0, 0, 0, 0.8);

            .banner-icon {
                font-size: 0.24rem;
            }
        }
    }
}
</style>

