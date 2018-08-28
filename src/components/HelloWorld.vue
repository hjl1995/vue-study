<template>
   <div class="app">
      <div class="outNode">
        <div class="topNode">
          <div class="left" @click="leftCl"></div>
          <div class="right" @click="rightCl"> </div>
          <div class="moveDiv">
            <ul :style='{width:img.length*800+"px",left:index*-800+"px"}'>
              <li v-for="i in img">
                <img :src="i">
              </li>
            </ul>
          </div>
          <div class="textDiv">
            <span class="text">{{msg[index]}}</span>
          </div>
        </div>
        <div class="bottomNode">
          <ol :style='{width:img.length*200+"px"}'>
            <li v-for='(i,needIndex) in img' :class='index==needIndex?"active":""' @click='Lick(needIndex)'>
              <img :src="i" alt="">
            </li>
          </ol>
        </div>
      </div>
   </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      index: 0,
      msg:['图片1', '图片2', '图片3', '图片4', '图片5'],
      img: [require('../../img/1.jpg'), require('../../img/2.jpg'), require('../../img/3.jpg'), require('../../img/4.jpg'), require('../../img/5.jpg')]
    }
  },
  methods: {
    Lick (a) {
      this.index = a
    },
    leftCl(){
      this.index--;
      if (this.index==-1){
        this.index=this.img.length-1;
      }
    },
    rightCl(){
      this.index++;
      if (this.index == this.img.length) {
        this.index = 0
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  *{
    margin: 0;
    padding: 0;
    list-style: none;
  }
  .topNode .moveDiv{
    width: 100%;
    height: 400px;
    float: left;
    position: relative;
    overflow: hidden;
  }
  .topNode .moveDiv>ul{
    height: 400px;
    position:absolute ;
    top: 0;
    left: 0;
  }
.topNode .moveDiv>ul>li{
  width: 800px;
  float: left;
  height: 100%;
  transition: .3s;
}
.topNode .moveDiv>ul>li img{
  width: 100%;
  height:100%;
}
.outNode{
  width: 800px;
  height: 640px;
  border: 1px solid red;
}
  .topNode{
    width: 100%;
    float: left;
    height: 440px;
    position: relative;
  }
  .topNode .left{
    width: 20px;
    height: 20px;
    border-radius: 50px;
    position: absolute;
    left: 10px;
    top: 50%;
    z-index: 5;
    cursor: pointer;
    background: rgb(255,255,255,0.7);

  }
  .topNode .right{
    width: 20px;
    height: 20px;
    border-radius: 50px;
    position: absolute;
    right: 10px;
    top: 50%;
    z-index: 5;
    cursor: pointer;
    background: rgb(255,255,255,0.7);

  }
  .topNode .textDiv{
    width: 100%;
    height: 40px;
    float: left;
    background: blue;
    line-height: 40px;
  }
  .text{
    font-size: 20px;
    float: left;
    color: white;
    padding-left: 10px;
  }
  .bottomNode{
    width:100%;float: left;height: 200px;
    position: relative;
    overflow: hidden;
  }
  .bottomNode>ol{
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
  }
  .bottomNode>ol>li{
    width: 160px;
    height:200px;
    float: left;
    box-sizing: border-box;
    border:10px solid cornflowerblue ;
    /*display: inline-block;*/
    transition: 0.3s;
  }
  .bottomNode>ol>li img{
    width: 100%;
    height: 100%;
  }
  .bottomNode>ol>li.active{
    border-color: orange;
  }
</style>
