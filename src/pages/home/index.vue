<template>
  <div class="xj-home">
    <van-swipe class="xj-swipe" :autoplay="3000" indicator-color="orange">
      <van-swipe-item>
          <img src="/static/home/banner1.jpg" width="100%" height="100%" alt="">
      </van-swipe-item>
      <van-swipe-item>
          <img src="/static/home/banner2.jpg" width="100%" height="100%" alt="">
      </van-swipe-item>
      <van-swipe-item>
          <img src="/static/home/banner3.jpg" width="100%" height="100%" alt="">
      </van-swipe-item>
      <van-swipe-item>
          <img src="/static/home/banner4.jpg" width="100%" height="100%" alt="">
      </van-swipe-item>
      <van-swipe-item>
          <img src="/static/home/banner5.jpg" width="100%" height="100%" alt="">
      </van-swipe-item>
      <van-swipe-item>
          <img src="/static/home/banner6.jpg" width="100%" height="100%" alt="">
      </van-swipe-item>
      <van-swipe-item>
          <img src="/static/home/banner7.jpg" width="100%" height="100%" alt="">
      </van-swipe-item>
      <van-swipe-item>
          <img src="/static/home/banner8.jpg" width="100%" height="100%" alt="">
      </van-swipe-item>
    </van-swipe>
    <div class='search'>搜索店铺、商品</div>
    <div class='city'>东莞市 ></div>
    <van-swipe class="xj-category" indicator-color="orange">
      <van-swipe-item>
          <ul>
              <li>
                  <div></div>
                  <span>百美达水业</span>
              </li>
              <li>
                  <div></div>
                  <span>私密大健康</span>
              </li>
              <li>
                  <div></div>
                  <span>旅游美食</span>
              </li>
              <li>
                  <div></div>
                  <span>网红直播</span>
              </li>
              <li>
                  <div></div>
                  <span>女性文化</span>
              </li>
              <li>
                  <div></div>
                  <span>时尚眼镜</span>
              </li>
              <li>
                  <div></div>
                  <span>房产租售</span>
              </li>
              <li>
                  <div></div>
                  <span>二手车买卖</span>
              </li>
              <li>
                  <div></div>
                  <span>帝王绿翡翠</span>
              </li>
              <li>
                  <div></div>
                  <span>平台招商</span>
              </li>
          </ul>
      </van-swipe-item>
      <van-swipe-item>
            <ul>
                <li>
                    <div></div>
                    <span>高服装鞋帽</span>
                </li>
                <li>
                    <div></div>
                    <span>智能机器人</span>
                </li>
                <li>
                    <div></div>
                    <span>模特明星</span>
                </li>
                <li>
                    <div></div>
                    <span>数码科技</span>
                </li>
                <li>
                    <div></div>
                    <span>一带一路</span>
                </li>
                <li>
                    <div></div>
                    <span>投资移民</span>
                </li>
                <li>
                    <div></div>
                    <span>防爆胎订购</span>
                </li>
                <li>
                    <div></div>
                    <span>文化艺术品</span>
                </li>
                <li>
                    <div></div>
                    <span>广告推广</span>
                </li>
                <li>
                    <div></div>
                    <span>保险金融</span>
                </li>
            </ul>
      </van-swipe-item>
    </van-swipe>

    <div class="xj-recommend"> — 推荐商家 — </div>
    <van-swipe :autoplay="3000" :show-indicators='false' class='xj-swipe-commend'>
        <van-swipe-item>
            <ul>
                <li>
                    <div class="xj-commend"></div>
                    <span>高尔夫俱乐部</span>
                </li>
                <li>
                    <div class="xj-commend"></div>
                    <span>百美达实业产品</span>
                </li>
                <li>
                    <div class="xj-commend"></div>
                    <span>世纪夫人</span>
                </li>
            </ul>
        </van-swipe-item>
        <van-swipe-item>
            <ul>
                <li>
                    <div class="xj-commend"></div>
                    <span>高尔夫俱乐部</span>
                </li>
                <li>
                    <div class="xj-commend"></div>
                    <span>百美达实业产品</span>
                </li>
                <li>
                    <div class="xj-commend"></div>
                    <span>世纪夫人</span>
                </li>
            </ul>
        </van-swipe-item>
    </van-swipe>    

    <div class="xj-tab">
        <van-sticky :offset-top="0">
        <div class="xj-top">
            <ul>
                <!-- <li class="current" >附近的店</li>
                <li>附近的店</li>
                <li>附近的店</li>
                <li>99元入驻</li> -->
                <li :class="activeClass == index ? 'active':''" v-for="(item,index) in itemList" :key="index" @click="getItme(index)">{{item.text}}
                </li>
                <li @click="get_in">99元入驻</li>
            </ul>
        </div>
        </van-sticky>

        <div class="xj-content">
            <div class="fujin" v-show='activeClass==activeClass'>
                <ul>
                    <li v-for="(item, index) in 3" :key="index">
                        <div class="left" @click="go_company"></div>
                        <div class="right">
                            <div class="name" @click="go_company">广州市宏伟管理有限公司</div>
                            <div style="color:#ffd21e" @click="go_company">
                                <van-rate readonly size='14' style="float:left"
                                    v-model="value"
                                    allow-half
                                    void-icon="star"
                                    void-color="#eee"
                                    /> <span>4.5</span>
                            </div>
                            <div class="distand" @click="go_company">
                                <span>1247浏览</span>
                                <span style="float:right">50km</span>
                            </div>
                            <div class="news">
                                <div>最新发布:图风扇电机佛is点击佛山店金佛山京东附近</div>
                                <span>2条消息></span>
                            </div>
                        </div>
                    </li>
                </ul>
            </div>
            <!-- <div class="renqi" v-show='activeClass==1'>
                 <ul>
                    <li v-for="(item, index) in 20" :key="index">
                        <div class="left" style="background:#7719aa"></div>
                        <div class="right">
                            <div class="name">广州市宏伟管理有限公司</div>
                            <div style="color:#ffd21e">
                                <van-rate readonly size='14' style="float:left"
                                    v-model="value"
                                    allow-half
                                    void-icon="star"
                                    void-color="#eee"
                                    /> <span>4.5</span>
                            </div>
                            <div class="distand">
                                <span>1247浏览</span>
                                <span style="float:right">50km</span>
                            </div>
                            <div class="news">
                                <div>最新发布:图风扇电机佛is点击佛山店金佛山京东附近</div>
                                <span>2条消息></span>
                            </div>
                        </div>
                    </li>
                </ul>
            </div>
            <div class="linquan" v-show='activeClass==2'>
                 <ul>
                    <li v-for="(item, index) in 20" :key="index">
                        <div class="left" style="background:pink"></div>
                        <div class="right">
                            <div class="name">广州市宏伟管理有限公司</div>
                            <div style="color:#ffd21e">
                                <van-rate readonly size='14' style="float:left"
                                    v-model="value"
                                    allow-half
                                    void-icon="star"
                                    void-color="#eee"
                                    /> <span>4.5</span>
                            </div>
                            <div class="distand">
                                <span>1247浏览</span>
                                <span style="float:right">50km</span>
                            </div>
                            <div class="news">
                                <div>最新发布:图风扇电机佛is点击佛山店金佛山京东附近</div>
                                <span>2条消息></span>
                            </div>
                        </div>
                    </li>
                </ul>
            </div> -->
        </div>
    </div>

    
    
  </div>
</template>
<script>

export default {
    data:function(){
        return{
            activeClass: 0,
            itemList:[
                {text:'附近的店'},
                {text:'人气排名'},
                {text:'领券排名'},
            ],
            value:4.5
        }
    },
    methods:{
        getItme(index) {
            this.activeClass = index;  // 把当前点击元素的index，赋值给activeClass
        },
        go_company(){
            this.jump('detail');
        },
        get_in(){
            this.jump('addstore');
        }
    }
};
</script>
<style lang="scss" scoped>
    .xj-home {
        // background: red;
        height: px2rem(154);
        position: relative;
    .xj-swipe {
        height: 100%;
    }

    .search{
            background-color: rgba(167, 168, 171,.5);
            width: px2rem(130);
            height: px2rem(30);
            border-radius: px2rem(30);
            z-index: 9999;
            position: absolute;
            left:px2rem(17);
            top: px2rem(12);
            text-align: center;
            line-height: px2rem(30);
            color: white;
            font-size: px2rem(14);
    }
    .city{
            background-color: rgba(167, 168, 171,.5);
            width: px2rem(70);
            height: px2rem(30);
            z-index: 9999;
            position: absolute;
            right:px2rem(17);
            top: px2rem(12);
            text-align: center;
            line-height: px2rem(30);
            color: white;
            font-size: px2rem(14);
            border-radius: px2rem(30);
    }
    //分类导航
    .xj-category{
        height: px2rem(180);
        li{
            width: 20%;
            height:50%;
            // margin-left: px2rem(9);
            margin-top: px2rem(15);
            float: left;
            text-align: center;
            position: relative;
            line-height: px2rem(20);
            div{
            background: blue;
            width: px2rem(42);
            height: px2rem(42);
            border-radius: 50%;
            margin:0 auto;
            }
        }
    }

        //
    .xj-recommend{
        height: px2rem(30);
        color:#242424;
        text-align: center;
        line-height: px2rem(30);
        font-size: px2rem(15);
    }
    .xj-swipe-commend{
        li{
            float: left;
            width: 33.33333333333333%;
            height: px2rem(120);
            line-height: px2rem(25);
            text-align: center;
            color: #5e5e5e
        }
        .xj-commend{
            width: px2rem(115);
            height: px2rem(80);
            background-color: red;
            margin: 5px auto;
            border-radius: px2rem(10);
        }
    }
    .xj-top{
        background-color: #fff;
        height: px2rem(33);
        // margin-top: px2rem(20);
        text-align: center;
        font-size: px2rem(14);
        font-weight: bold;
        border-top: 1px #eeeeee solid;
        border-bottom: 1px #eeeeee solid;
        padding-top:12px;
            li{
                height: px2rem(25);
                color: #5e5e5e;
                float: left;
                width: 25%;
                line-height: px2rem(25);
            }
            li:last-child{
                color: white;
                background-color: orange;
                border-radius: px2rem(25);
                margin: auto auto;
            }
            .active {
                color: orange;
            }
        
    }

    .xj-content{
        
        li{
            width: 100%;
            height: px2rem(115);
            // background-color: red;
            border-bottom: px2rem(5) #f4f4f4 solid;
            position: relative;
            .left{
                position: absolute;
                left: px2rem(15);
                top: px2rem(15);
                height: px2rem(65);
                width: px2rem(65);
                background-color: green;
                border-radius: px2rem(5);
            }
            .right{
                // float: left;
                // width: 80%; 
                padding-top: px2rem(12);
                padding-left: px2rem(95);
                padding-right: px2rem(15);
                .name{
                    margin-bottom: px2rem(5);
                    font-weight: bold;
                    font-size: px2rem(16);
                }
                div:nth-child(2){
                    position: relative;
                    overflow: hidden;
                    span{
                        // position:absolute;
                        float: left;
                        // left: 25%;
                        // display: block;
                        // top: px2rem(-2);
                        padding-left: px2rem(3);
                        // padding-top:  px2rem(5);
                        font-size: px2rem(14);
                    }
                }
                .distand{
                    padding-top: px2rem(5);
                    padding-bottom: px2rem(4);
                    border-bottom: px2rem(1) #f3f3f3 solid;
                    color: #838182;
                }
                .news{
                    div{
                        line-height: px2rem(32);
                        float: left;
                        overflow: hidden;
                        text-overflow:ellipsis;
                        white-space: nowrap;
                        width: 60%;
                    }
                    span:last-child{
                        line-height: px2rem(32);
                        float: right;
                    }
                }
            }
        }
    }


  



}
</style>
