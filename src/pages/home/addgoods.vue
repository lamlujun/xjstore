<template>
    <div class="add-goods">
        <!-- 商品名称 -->
        <div class="goods-name">
            <div class="goods-text">
                    <span>商品名称</span>
            </div>

            <div class="mid">
                    <van-cell-group>
                        <van-field style="width:5rem;" v-model="username" placeholder="请输入商品名称"/>
                    </van-cell-group>
            </div>
        </div>

        <!-- 价格 -->
        <div class="goods-name">
            <div class="goods-text">
                    <span>价　　格</span>
            </div>

            <div class="mid">
                    <van-cell-group>
                        <van-field type="number" style="width:5rem;" v-model="price" placeholder="请输入商品价格"/>
                    </van-cell-group>
            </div>
        </div>

        <!-- 原价 -->
        <div class="goods-name">
            <div class="goods-text">
                    <span>原　　价</span>
            </div>

            <div class="mid">
                    <van-cell-group>
                        <van-field type="number" style="width:5rem;" v-model="before_price" placeholder="请输入商品原价"/>
                    </van-cell-group>
            </div>
        </div>

         <!-- 规格 -->
        <div class="goods-name">
            <div class="goods-text">
                    <span>规　　格</span>
            </div>

            <div class="mid">
                    <van-cell-group>
                        <van-field style="width:5rem;" v-model="specs" placeholder="请输入商品规格"/>
                    </van-cell-group>
            </div>
        </div>

        <!-- 商品简介 -->
        <div class="store-introduce">
            <div class="goods-text">
                    <span>商品介绍</span>
            </div>

            <div class="inpro-text">
                <van-cell-group>
                    <van-field 
                        style="width:5.3rem"
                        v-model="introduce"
                        rows="6"
                        autosize
                        type="textarea"
                        placeholder="请输入商品简介"
                    />
                </van-cell-group>
            </div>
        </div>

        <div class="store-pic">
             <div class="goods-text">
                    <span>商品图片</span>
            </div>

            <div class="right-pic">
                <div class="bot-upload">
                    <van-uploader v-model="goodspic" multiple  :max-count="9"/>
                </div>
            </div>
        </div>

        <div class="btn-submit">
            提交
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            username:'',
            price:"",
            before_price:'',
            specs:'',
            introduce:'',
            goodspic:[],

        }
    },
    methods:{
            
    }
}
</script>

<style lang="scss" scoped>
    .add-goods{
        padding-bottom: px2rem(40);
    }
    .goods-name{
        height: px2rem(50);
        border-bottom: px2rem(2) #f4f4f4 solid;
        .input-name{
            float: left;
            width: 70%;
            height: 100%;
            padding-left: px2rem(11);
        }
    }
    .mid{
        float: left;
        width: 70%;
        height: px2rem(50);
        display: flex;
        align-items: center;

    }
    .store-introduce{
            height: px2rem(170);
            border-bottom: px2rem(10) #f5f5f5 solid;
            .inpro-text{
                float: left;
                height: px2rem(170);
            }
        }
    .goods-text{
        float: left;
        width: 25%;
        font-size: px2rem(16);
        // font-weight: bold;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .btn-submit{
            height: px2rem(40);
            background-color: #fd7a29;
            text-align: center;
            line-height: px2rem(40);
            font-size: px2rem(16);
            color: #fff;
            position: fixed;
            bottom: 0;
            width: 100%;
        }

    .store-pic{
            padding-top: px2rem(10);
            .right-pic{
                float: left;
                width: 71%;
                padding-left: px2rem(11);
                // height: px2rem(170);
                // background-color: red;    
                .top-text{
                    height: px2rem(50);
                    line-height: px2rem(50);
                    font-size: px2rem(14);
                    color: #a6a6a6;


                }            
            }
        }
</style>