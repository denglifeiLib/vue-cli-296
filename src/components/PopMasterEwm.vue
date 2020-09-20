<template>
    <!-- 预约成功 -->
    <mt-popup v-model="popInfo.show" position="center" class="mint-popup master_ewm_pop">
        <div class="master_ewm_wrap">
            <img src="../assets/images/bzrewmbg@2x.png" alt="" class="img">
            <img src="../assets/images/close.png" alt="" class="close" @click="popInfo.show=false">
            <p class="blue f16">请添加班主任微信</p>
            <div class="flex_box kefu_alert">
                <div class="item">
                    <img src="../assets/images/header.jpg" alt="" class="ewm">
                    <p class="text_dis">班主任微信二维码</p>
                    <p class="text_dis btm_dis">请长按二维码保存至相册</p>
                    <!-- <button class="btn plain_blue">保存</button> -->
                </div>
                <div class="item">
                    <div class="weixin_info flex_box">
                        <img src="../assets/images/wx@2x.png" alt="" class="weix">
                        <p class="name">cike001</p>
                    </div>
                    <p class="text_dis">班主任微信账号</p>
                    <button class="btn plain_blue">复制</button>
                </div>
            </div>
        </div>
    </mt-popup>
</template>

<script>

export default({
    data(){
        return {
           showPop: false 
        }
    },
    props:{
        popInfo:{ 
            type: Object,
            default(){
                return {

                }
            }
        },
        showSkip:{ 
            type: Boolean,
            default: false
        },
        showClose:{ 
            type: Boolean,
            default: false
        },
        title:{ 
            type: String,
            default: ''
        },
    },
    created() {
        this.showPop = this.show
    },
    computed:{

    },
    methods: {
        change(q) {
            this.$emit('qqqqq', q)
        }, 
        skip() {
            this.$emit('skip')
        }, 
        close() {
            this.$emit('cancel')
        }
    }
})
</script>

<style lang="less">
.master_ewm_pop{
 border-radius: 12px;
overflow: hidden;
}
.master_ewm_wrap{
    position: relative;
        width: 311px;
        padding-bottom: 48px;
        background: #FFFFFF;
       text-align: center;
       .close{
           position: absolute;
           width: 14px;
           top:11px;
           right: 11px;
       }
        .img{
            display: block;
            width: 311px;
        }
        .kefu_alert{
            // padding: 29px 0 40px;
            padding-top: 25px;
            justify-content: space-around;
            .item, .ewm, .weixin_info{
                width:110px;
                height:110px;
                text-align: center;
            }
            .item{
                height: auto;
                &:first-child{
                    width: 132px;
                }
                .btn{
                    margin: 15px auto 0;
                    width:68px;
                    height:27px;
                }
                .btm_dis{
                    margin-top: 15px;
                }
            }
            .weixin_info{
                flex-direction: column;
                justify-content: center;
                align-items: center;
                .weix{
                    width: 29px;
                    margin-bottom: 12px;
                }
                
            }

        }
    }

    


</style>