<template>
    <div class="icons">
        <swiper>
        <swiper-slide v-for="(page,index) of pages" :key="index">
            <div 
                class="icon" 
                v-for="item of page"
                :key="item.id"
              >
                <div class="icon-img">
                    <img class="icon-img-content" :src='item.imgUrl' alt="">
                
                </div>
                <p class="icon-desc">{{item.desc}}</p>
            </div> 
        </swiper-slide>
        </swiper>
    </div>

</template>

<script> 
    export default{
        name: 'HomeIcons',
        props:{
            list:Array
        },
        computed: {
            pages () {
                const pages = []
                this.list.forEach((item, index) =>{
                    const page= Math.floor(index / 8)
                    if (!pages[page]) {
                        pages[page]=[]
                    }
                    pages[page].push(item)
                })
                return pages
            }
        }
    }
</script>

<style lang="stylus" scoped>
  @import '../../assets/styles/varibles.styl'
  @import '../../assets/styles/mixins.styl'
  .icons >>>.swiper-container
    height:0
    padding-bottom: 50%
    /*这里用icon标签给每个图标设置占位大小，并且设置浮动，因此能够排列下去*/
    .icon
      position: relative
      overflow: hidden
      float: left
      width:25%
      height: 0
      padding-bottom: 25%
      .icon-img
        position: absolute
        top:0
        left: 0
        right: 0
        bottom: .3rem
        box-sizeing:border-box
        padding:.3rem
        .icon-img-content
          display: block
          margin:0 auto
          height: 100%
      .icon-desc
        position: absolute
        height: .44rem
        left: 0
        right: 0
        bottom: 0
        line-height: .44rem
        color:$darkTextColor
        text-align:center
        ellipsis()

        

</style>