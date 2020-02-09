<template>
    <div class="add-store">
        <div class="top-pic"></div>
        <div class="store-head">
            <div class="store-text">
                    <span>店铺头像</span>
                    
            </div>
            <div class="right-text">
                <van-uploader
                    v-model="headpic" :before-read="beforeRead"
                    multiple
                    :max-count="1"
                    image-fit="contain"
                    preview-size='1.6rem'
                />
            </div>
        </div>
        <div class="store-name">
            <div class="store-text">
                    <span>店铺名称</span>
            </div>

            <div class="mid">
                    <van-cell-group>
                        <van-field v-model="username" placeholder="请输入店铺名称" maxlength="8" show-word-limit/>
                    </van-cell-group>
            </div>
        </div>

        <div class="store-address">
            <div class="store-text">
                    <span>店铺地址</span>
            </div>

            <div class="input-address">
                <div class="mid">
                    <van-cell-group>
                        <van-field style="width:3.5rem" v-model="address" placeholder="请输入店铺地址" />
                    </van-cell-group>
                </div>
               <!-- <input type="text" placeholder="请输入店铺地址" maxlength="8" style="border:none;"> -->
               <div class="set-address">
                    <div>设置定位</div>
               </div>
            </div>
        </div>

        <div class="store-app">
            <div class="store-text">
                    <span>店内设施</span>
            </div>

            <div class="select-box">
                <div class="left">
                    <van-checkbox-group v-model="result">
                        <van-checkbox name="wifi" style="margin-top:0.4rem" icon-size='0.45rem'>WIFI</van-checkbox>
                        <van-checkbox name="alipay" style="margin-top:0.4rem" icon-size='0.45rem'>支付宝支付</van-checkbox>
                    </van-checkbox-group>
                </div>
                <div class="right" style="float:left">
                    <van-checkbox-group v-model="result">
                        <van-checkbox name="car" style="margin-top:0.4rem" icon-size='0.45rem'>停车位</van-checkbox>
                        <van-checkbox name="wx" style="margin-top:0.4rem" icon-size='0.45rem'>微信支付</van-checkbox>
                    </van-checkbox-group>
                </div>
            </div>

        </div>

        <div class="store-time">
             <div class="store-text">
                    <span>营业时间</span>
            </div>

            <div class="left">
                <van-field
                    readonly
                    clickable
                    :value="startime"
                    placeholder="请选择"
                    @click="showPicker = true"
                />

                <van-popup v-model="showPicker" position="bottom">
                    <van-datetime-picker
                        v-model="startime"
                        type="time"
                        :min-hour="0"
                        :max-hour="23"
                        @cancel="showPicker = false"
                        @confirm="onConfirm"
                    />
                </van-popup>
            </div>

            <div class="time-mid">
                至
            </div>

            <div class="left">
                <van-field
                    readonly
                    clickable
                    :value="endtime"
                    placeholder="请选择"
                    @click="showEnd = true"
                />

                <van-popup v-model="showEnd" position="bottom">
                    <van-datetime-picker
                        v-model="endtime"
                        type="time"
                        :min-hour="0"
                        :max-hour="23"
                        @cancel="showEnd = false"
                        @confirm="endtimes"
                    />
                </van-popup>
            </div>

        </div>

        <div class="store-introduce">
            <div class="store-text">
                    <span>店铺简介</span>
            </div>

            <div class="inpro-text">
                <van-cell-group>
                    <van-field 
                        style="width:5.3rem"
                        v-model="introduce"
                        rows="6"
                        autosize
                        type="textarea"
                        placeholder="请输入店铺简介"
                    />
                </van-cell-group>
            </div>
        </div>

        <div class="store-pic">
             <div class="store-text">
                    <span>店铺图片</span>
            </div>

            <div class="right-pic">
                <div class="top-text">为保证显示效果,建议上传三张图片</div>
                <div class="bot-upload">
                    <van-uploader v-model="storepic" multiple :max-count="3" />
                </div>
            </div>
        </div>

        <div class="choose-cate">
            <div class="store-text">
                    <span>选择分类</span>
            </div>

            <div class="show-cate">
                <van-field
                    readonly
                    clickable
                    :value="category"
                    placeholder="请选择入驻分类"
                    @click="showCate = true"
                />
                <van-popup v-model="showCate" position="bottom">
                    <van-picker
                        show-toolbar
                        :columns="columns"
                        @cancel="showCate = false"
                        @confirm="showCates"
                    />
                </van-popup>
            </div>
        </div>

        <div class="agree">
            <div class="agree-div">
                <van-checkbox v-model="agree" shape="square">我已阅读并同意<a href="#"> 平台用户服务协议 </a></van-checkbox>
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
            headpic: [],
            storepic:[],
            result: [],
            username: "",
            address: "",
            startime:"",
            endtime:"",
            showPicker:false,
            showEnd:false,
            showCate:false,
            introduce:"",
            category:"",
            columns: ['不选择分类', '百美达水业', '思密大健康', '女性文化', '网红直播','时尚眼镜'],
            agree:"",
        }
    },
    methods:{
            // 返回布尔值
            beforeRead(file) {
                if (file.type !== 'image/jpeg') {
                    this.$toast('请上传 jpg 格式图片');
                    return false;
            }
    
                return true;
            },
            onConfirm(value) {
                this.startime = value;
                this.showPicker = false;
            },
            endtimes(value){
                this.endtime = value;
                this.showEnd = false;
            },
            showCates(value){
                this.category= value;
                this.showCate = false;
            }
            
            
    }
}
</script>

<style lang="scss" scoped>
    .add-store{
        padding-bottom: px2rem(40);
        //顶部图片
        .top-pic{
            height: px2rem(70);
            background: url('/static/store/storeinformation.jpg') no-repeat;
            background-size: 100% 100%;
        }
        //店铺头像
        .store-head{
            height: px2rem(100);
            border-bottom: px2rem(1) #ededed solid;
            .right-text{
                float: left;
                width: 70%;
                padding-top:px2rem(10);
                padding-left: px2rem(11);
            }
        }
        .store-name{
            height: px2rem(50);
            .input-name{
                float: left;
                width: 70%;
                height: 100%;
                padding-left: px2rem(11);
            }
        }
        .mid{
            float: left;
            width: 52%;
            height: px2rem(50);
            display: flex;
            align-items: center;

        }
        .store-address{
            border-top: px2rem(10) #f5f5f5 solid;
            border-bottom: px2rem(10) #f5f5f5 solid;
            height: px2rem(50);
            .set-address{
                width: 23%;
                height: px2rem(50);
                float: right;
                text-align: center;
                display: flex;
                justify-content: center;
                align-items: center;
                div{
                    width: 80%;
                    height: px2rem(23);
                    color: #fff;
                    background-color: #fa7928;
                    border-radius: px2rem(21);
                    line-height: px2rem(23);
                 }
            }
        }

        .store-app{
            height: px2rem(96);
            border: px2rem(1) #f4f4f4 solid;
            .select-box{
                font-size: px2rem(14);
                float: left;
                padding-left: px2rem(11);
                .left{
                    margin-right: px2rem(25);
                    float: left;
                }
            }
        }

        .store-time{
            height: px2rem(50);
            border-bottom: px2rem(10) #f5f5f5 solid;
            .left{
                height: px2rem(50);
                width: 20%;
                display: flex;
                float: left;
                align-items: center;
            }
            .time-mid{
                height: px2rem(50);
                float: left;
                display: flex;
                align-items: center;
            }
        }

        .store-introduce{
            height: px2rem(170);
            border-bottom: px2rem(10) #f5f5f5 solid;
            .inpro-text{
                float: left;
                height: px2rem(170);
            }
        }

        .store-pic{
            height: px2rem(130);
            border-bottom: px2rem(10) #f5f5f5 solid;
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

        .choose-cate{
            height: px2rem(50);
            .show-cate{
                height: px2rem(50);
                display: flex;
                float: left;
                align-items: center;
            }

        }


        .agree{
            height: px2rem(50);
            background-color: #f4f4f4;
            padding-top: px2rem(15);
            padding-left: px2rem(15);
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

        .store-text{
            float: left;
            width: 25%;
            font-size: px2rem(16);
            font-weight: bold;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
        }


    }
</style>