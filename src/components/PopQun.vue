<template>
    <div class="qun_pop">
        <img src="../assets/images/xuanfuguanbi@2x.png" alt="" class="close" @click="$emit('hide')">
        <img src="../assets/images/banjiqun_xfu@2x.png" alt="" class="img" @click="$emit('handlClick')">
    </div>
</template>

<script>

export default({
    data(){
        return {
           showPop: false 
        }
    },
    props:{
        showQunPop:{ 
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
.qun_pop{
    position: fixed;
    bottom: 70px;
    right: 2px;
    z-index: 8888;
    .img{
        width: 50px;
    }
    .close{
        position: absolute;
        width: 16px;
        top: -11px;
        right: 0;
    }
}


</style>