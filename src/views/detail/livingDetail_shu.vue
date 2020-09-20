<template>
    <div class="living_detail_shu_page">
        <div class="flex_box yuyue_bar" v-if="showYuyueBar">
            <div class="bd bold"><span class="red">08-24 20:00</span> 开始直播</div>
            <button class="btn plain_red ft">预约直播</button>
        </div>

        <div class="out_teacher_box">
            <div class="teacher_box flex_box">
                <img src="../../assets/images/default1.jpg" alt="" class="header bd">
                <div class="bd white"><span class="f13">lulu 老师</span><br><span class="f11">12324 观看</span></div>
                <button class="btn white ft">关注</button>
            </div>
        </div>

       <div class="living_hook" :class="{with_yuyue_bar: showYuyueBar}"></div>

        <mt-popup v-model="showDetail" position="bottom" class="mint-popup common_pop_wrap">
            <div class="detail_pop">
                <img src="../../assets/images/xiangq_close@2x.png" alt="" class="close" @click="showDetail=false">
                <tabs :list="tabList" :active="activeTab" @change="changeTab"></tabs>
                <div class="cont">
                    <router-view ></router-view> 
                </div>
            </div> 
        </mt-popup>
        

        <div class="view_detail_bar flex_box" @click="showDetail=true">
            <img src="../../assets/images/xiangqing@2x.png" alt="" class="ft icon">
            <span class="ft">详情介绍</span>
        </div>
        <div class="btm_fixed flex_box">
            <p class="text_dis bd">
                <span class="f14 red">¥</span>
                <span class="f20 red"> {{isFree ? '免费' : 29.6}}</span>
                <span class="f14 originPrice" v-if="!isFree">88</span>
            </p>
            <button class="btn red ft">
                加入学习
                <img src="../../assets/images/icon_right_w@2x.png" alt="" class="icon">
            </button>
        </div>
    </div>
</template>

<script>
import Tabs from '@/components/Tabs';
import PopWrap from '@/components/PopWrap';
import * as Axios from '@/utils/Action';
export default {
    name: 'test',
    data() {
        return {
            showDetail: false,
            showYuyueBar: true,
            tabList: [
                {
                    label: '课程介绍',
                    value: 'ke_jieshao'
                }, {
                    label: '课程目录',
                    value: 'ke_mulv'
                }, {
                    label: '课程推荐',
                    value: 'ke_tuijian'
                }, {
                    label: '评价（114）',
                    value: 'pingjia'
                }, {
                    label: '直播介绍',
                    value: 'zhibo_jieshao'
                }, {
                    label: '直播推荐',
                    value: 'zhibo_tuijian'
                }
            ],
            activeTab: 0,
            isFree: false
        }
    },
    created() {
        this.$emit('header', {
            show: true,
            title: '首页',
            back: '0'
        });
        this.$emit('tabbar', {
            show: false
        })
    },
    methods: {
       changeTab(index, {value}) {
            this.activeTab = index;
            switch (value) {
                case 'ke_jieshao':
                    this.$router.replace('class');
                    break;
                case 'zhibo_jieshao':
                    this.$router.replace('class');
                    break;
                case 'ke_mulv':
                    this.$router.replace('menue');
                    break;
                case 'ke_tuijian':
                    this.$router.replace('introduce');
                    break;
                case 'zhibo_tuijian':
                    this.$router.replace('introduce');
                    break;
                case 'pingjia':
                    this.$router.replace('comment');
                    break;
            }
        },
    },
    components: {Tabs, PopWrap}
}
</script>

<style lang="less" scoped>
.living_detail_shu_page{
    .yuyue_bar{
        height: 52px;
        padding: 0 16px;
        background: #F2F4FC;
        font-size: 16px;
        .btn{
            padding-left: 28px;
            padding-right: 28px;
        }
    }

    .view_detail_bar{
        position: fixed;
       left: -0;
       right: 0;
       bottom: 48px;
        height: 44px;
        background: rgba(0, 0, 0, 0.6);
        justify-content: center;
        color: #fff;
        font-weight: bold;
        .icon{
            height: 16px;
            margin-right: 7px;
        }
    }

    .out_teacher_box{
        padding-left: 16px;
        height: 0;
    }
    .teacher_box{
        display: inline-flex;
        padding: 0 8px 0 3px;

height: 40px;
        margin-top: 16px;
        min-width: 190px;
        background: rgba(0, 0, 0, 0.25);
        border-radius: 23px;
        .header{
            width: 34px;
            height: 34px;
            padding: 0;
            border-radius: 34px;
        }
        .btn.white{
            min-width: auto;
        }
    }

    .btm_fixed{
       position: fixed;
       left: -0;
       right: 0;
       bottom: 0;
       height: 48px;
       padding: 0 16px 0 24px;
        z-index: 888;
        background: #FFFFFF;
        box-shadow: 0px -1px 0px 0px #E4E4E4;
       .originPrice{
           margin-left: 16px;
            border-bottom: solid 1px #949BA5;
            line-height: 0.1;
            display: inline-block;
        }
        .btn{
            height: 36px;
            width: 103px;
            .icon{
                margin-left: 8px;
                width: 5px;
            }
        }
   }

    .living_hook{
        height: 100vh;
        padding-bottom: 48px;
        background: orange;
        &.with_yuyue_bar{
            height: calc(100vh - 52px);
        }
   }

   .detail_pop{
       height: 68vh;
       width: 375px;
    //    overflow-x: hidden;
        position: absolute;
        background: #fff;
        left: 0;
        right: 0;
        bottom: 0;
        border-radius:12px 12px 0px 0px;
        .tabs{
            padding: 0 16px;
        }
        .close{
            position: absolute;
            width: 32px;
            height: 28px;
            top: -28px;
            right: 10px;
        }
        .cont{
            height: calc(68vh - 60px);
            overflow: scroll;
        }
   }
}
   
</style>