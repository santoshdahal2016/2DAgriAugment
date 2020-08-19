<template>
  <div class="container">
    <div class="header">
      <div class="logo" style="color: green;font-weight: bolder;">
        Agri Augment
      </div>
      <p id="reset" @click="clear()">Reset</p>

    </div>
    <div class="content-wrapper">
      <div class="list-wraper" style="overflow: scroll;height: 7  00px;">
        <div :key="item.id" v-for="item in list" class="image-wrapper"
          @click="handleAdd(item.url)">
          <img :src="item.url" />
          <i class="pt-iconfont icon-plus-circle"></i>
        </div>
      </div>
      <vue-fabric ref="canvas"
        :width="width" :height="height"
        @selection:created="selected"
        @selection:updated="selected"></vue-fabric>
      <div class="tool-wrapper">
        <i @click="handleDelete" class="pt-iconfont icon-delete"></i>
        <i @click="rotate" class="pt-iconfont icon-shuaxin"></i>
        <i @click="createImg" class="pt-iconfont icon-crop"></i>
      </div>
    </div>
    <vue-image-model :close="()=>{imgUrl=''}" v-show="imgUrl.length>0"
      :url="imgUrl"></vue-image-model>
  </div>
</template>

<script>
import VueImageModel from './image-model.vue';

export default {
  name: 'editor',
  components: {
    VueImageModel
  },
  data() {
    return {
      // http://data618.oss-cn-qingdao.aliyuncs.com/ys/3524/img/b.jpg
      imgUrl: '',
      width: 300,
      height: 500,
      list: [
        {
          id: 1,
          url: '/images/sticker7.png'
        },
        {
          id: 2,
          url: '/images/sticker2.png'
        },
        {
          id: 3,
          url: '/images/sticker3.png'
        },
        {
          id: 4,
          url: '/images/sticker4.png'
        }
      
      ]
    };
  },
  created() {
    this.width = 1024;
    this.height = 768;
    console.log(document.body.offsetWidth);
  },
  mounted() {
  

    this.$refs.canvas.setBackgroundImage('https://contentgrid.homedepot-static.com/hdus/en_US/DTCCOMNEW/Articles/paints-and-stains-for-your-concrete-basement-and-garage-floors-section-2.jpg');
    // this.$refs.canvas.createImage('/images/sticker2.png');
    // this.$refs.canvas.createImage('/images/sticker3.png');
    const options = {
      x: 100, y: 100, x1: 600, y1: 600, color: '#B2B2B2', drawWidth: 2, id: 'Triangle'
    };
    // this.$refs.canvas.createEllipse({ rx: 200, ry: 400, left: 300 });
    this.$refs.canvas.createTextbox('@Agri Augment', { top: 600, left: 900 });
    // this.$refs.canvas.setCornerIcons({ size: 20, tl: '/images/cow.png' });
  },
  methods: {
    clear(){
      this.$refs.canvas.clear();
      this.$refs.canvas.setBackgroundImage('https://contentgrid.homedepot-static.com/hdus/en_US/DTCCOMNEW/Articles/paints-and-stains-for-your-concrete-basement-and-garage-floors-section-2.jpg');
      this.$refs.canvas.createTextbox('@Agri Augment', { top: 600, left: 900 });

    },
    handleAdd(url) {
      // this.$refs.canvas.createTextbox('@Agri Augment', { top: 600, left: 900 });

      this.$refs.canvas.createImage(url);
    },
    handleDelete() {
      this.$refs.canvas.removeCurrentObj();
    },
    rotate() {
      this.$refs.canvas.setRotate();
    },
    createImg() {
      const dataUrl = this.$refs.canvas.toDataUrl();
      // console.log(dataUrl);

      this.imgUrl = dataUrl;
    },
    selected(obj, option) {
      console.log(obj);
      console.log(option);
    }
  }
};
</script>

<style lang='less' scoped>


#reset {
    background-color: black;
    color: white;
    display: block;
    height: 40px;
    line-height: 40px;
    text-decoration: none;
    width: 100px;
    text-align: center;
    cursor: grab;
}

.container {
  width: 100%;
  position: relative;
  height: 100%;
  display: flex;
  flex-direction: column;

  .header {
    height: 60px;

    border-bottom: 1px solid #efefef;
    display: -ms-flexbox;
    display: -moz-box;
    display: -webkit-box;
    display: -webkit-flex;
    display: flex;

    box-sizing: border-box;
    width: 100%;

    .logo {
      width: 200px;
      box-sizing: border-box;
      border-right: 1px solid #efefef;
      height: 60px;
      display: -ms-flexbox;
      display: -moz-box;
      display: -webkit-box;
      display: -webkit-flex;
      display: flex;
      box-align: center;
      -moz-box-align: center;
      -webkit-box-align: center;
      -webkit-align-items: center;
      align-items: center;
      box-pack: center;
      -moz-box-pack: center;
      -webkit-justify-content: center;
      justify-content: center;
    }
  }

  .content-wrapper {
    position: relative;
    display: -webkit-flex;
    display: -ms-flexbox;
    display: -moz-box;
    display: -webkit-box;
    display: flex;
    -moz-box-flex: 1;
    box-flex: 1;
    -webkit-box-flex: 1;
    -webkit-flex: 1;
    flex: 1;

    .tool-wrapper {
      position: absolute;
      top: 0;
      right: 0;
      display: -ms-flexbox;
      display: -moz-box;
      display: -webkit-box;
      display: -webkit-flex;
      display: flex;

      -webkit-box-orient: vertical;
      -webkit-box-direction: normal;
      -moz-box-direction: normal;
      -moz-box-orient: vertical;
      -webkit-flex-direction: column;
      flex-direction: column;

      .pt-iconfont {
        padding: 20px 30px;
      }
    }

    .list-wraper {
      width: 200px;

      border-right: 1px solid #efefef;
      overflow-y: auto;
      flex-shrink: 0;
      box-sizing: border-box;

      display: -webkit-flex;
      display: -ms-flexbox;
      display: -moz-box;
      display: -webkit-box;
      display: flex;
      -webkit-box-orient: vertical;
      -moz-box-orient: vertical;
      -webkit-flex-direction: column;
      flex-direction: column;

      .image-wrapper {
        padding: 20px;
        display: -ms-flexbox;
        display: -moz-box;
        display: -webkit-box;
        display: -webkit-flex;
        display: flex;

        flex-shrink: 0;
        box-pack: center;
        -webkit--moz-box-pack: center;
        -moz-box-pack: center;
        -webkit-justify-content: center;
        justify-content: center;
        box-align: center;
        -moz-box-align: center;
        -webkit-box-align: center;
        -webkit-align-items: center;
        align-items: center;
        border-bottom: 1px solid #efefef;
        position: relative;
        img {
          width: 120px;
        }
        .pt-iconfont {
          position: absolute;
          top: 0px;
          right: 0px;
          font-size: 18px;
          color: #777;
          padding: 10px;
        }
      }
    }
  }
}
</style>
