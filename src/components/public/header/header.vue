<template>
  <!-- 公用头部 -->
  <div class="header">
    <!-- 左半部分 -->
    <div class="header-left">
        <img :src="logo" alt="" srcset="">
        <div class="text">
          机场交通安全管理平台
        </div>
    </div>
    <!-- 右半部分 -->
    <div class="header-right">
      <!-- 搜索框 -->
      <div class="serching">
          <form action="javascript:;">
            <input class="serch-input" type="text" placeholder="搜索...">
            <a class="serch-btn">
              
            </a>
          </form>
      </div>
      <!-- 分割线 -->
      <div class="split"></div>
      <!-- 铃铛 -->
      <div class="bell" @click="showWarning">
        <div class="red-point" v-show="hasLog"></div>
      </div>
      <!-- 分割线 -->
      <div class="split"></div>
      <!-- 用户信息 -->
      <div class="user-info">
        <div class="left">
          <img :src="header" alt="">
        </div>
        <div class="middle">
            <div>
              {{userName}}
            </div>
            <div>
              {{department}} {{job}}
            </div>
        </div>
        <div class="right">
            <img src="../../../assets/header/箭头@2x.png" alt="">
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="stylus">
::-webkit-input-placeholder { /* WebKit browsers */
  font-family:PingFangSC-Regular;
  font-weight:400;
  color:#999999;
  font-size: 14px;
}

::-moz-placeholder { /* Mozilla Firefox 19+ */
  font-family:PingFangSC-Regular;
  font-weight:400;
  color:#999999;
  font-size: 14px;
}

:-ms-input-placeholder { /* Internet Explorer 10+ */
  font-family:PingFangSC-Regular;
  font-weight:400;
  color:#999999;
  font-size: 14px;
}   
  //头部公共样式
  .header
    width:100%;
    height:64px;
    background:rgba(255,255,255,1);
    // background-color black
    box-shadow:0px 3px 10px 0px rgba(0,0,0,0.03);
    box-sizing border-box
    padding-left 31px
    padding-right 30px
  .header:after
    clear:both
    content:''
    display block
  //左半部分样式
  .header-left
    float left
  .header-left:after
    clear:both
    content:''
    display block
  .header-left img 
    margin-top 14px;
    height 38px;
    width 38px;
    float left;
  .header-left .text
    float left
    width:238px;
    height:28px;
    font-size:20px;
    font-family:PingFangSC-Medium;
    font-weight:500;
    color:rgba(68,68,68,1);
    line-height:28px;
    letter-spacing:1px;
    margin-top:18px;
    text-align left;
    margin-left 8px;
  //右半部分样式
  .header-right
    float right;
    position relative
  .header-right:after
    clear:both
    content:''
    display block
  .header-right .serching
    margin-right 330px;
    margin-top:15px;
    position relative;
    float right;
  .header-right .serching .serch-input
    width:280px;
    height:34px;
    background:#F7F7F7;
    border-radius:2px;
    border 0;
    padding-left 10px;
    box-sizing border-box;
    font-size:14px;
    font-family:PingFangSC-Regular;
    font-weight:400;
    color:#999999;
  .header-right .serching .serch-btn
    display inline-block
    width 20px
    height 20px;
    background url('../../../assets/header/搜索@2x.png') center center no-repeat;
    background-size contain;
    position absolute;
    right 10px;
    top 7px;
    cursor pointer;
  //分割线
  .header-right .split
    width:1px;
    height:20px;
    background:rgba(229,229,229,1);
    position absolute;
    right 299px;
    top:22px;
  //铃铛
  .header-right .bell
    display inline-block
    width 22px
    height 22px;
    background url('../../../assets/header/预警@2x.png') center center no-repeat;
    background-size contain;
    position absolute;
    right 249px;
    top 21px;
    cursor pointer;
  .header-right .bell .red-point
    display inline-block
    width 10px
    height 10px;
    background url('../../../assets/header/Oval 2@2x.png') center center no-repeat;
    background-size contain;
    position absolute;
    top -4px;
    right -4px;
    cursor pointer;
  //分割线2
  .header-right .split:last-child
    width:1px;
    height:20px;
    background:rgba(229,229,229,1);
    position absolute;
    right 228px;
    top:22px;
  //用户信息
  .header-right .user-info
    position absolute
    width auto;
    right 0;
    top 12px;

  .header-right .user-info:after
    display block;
    content '';
    clear both;
  .header-right .user-info .left
    width 36px;
    height 36px;
    float left;
  .header-right .user-info .left img
    width 36px;
    height 36px;
    border-radius:50%;
  .header-right .user-info .middle
    float left;
    margin-left 10px;
    width 112px;
  .header-right .user-info .middle div:first-child
    font-size:14px;
    font-family:PingFangSC-Medium;
    font-weight:500;
    color:rgba(68,68,68,1);
    text-align left ;
  .header-right .user-info .middle div:last-child
    width 112px; 
    font-size:12px;
    font-family:PingFangSC-Regular;
    font-weight:400;
    color:rgba(68,68,68,1);
    line-height:16px;
    margin-top:2px;
  .header-right .user-info .right
    float left;
    margin-left 10px;
    width 30px;
    height 30px;
  .header-right .user-info .right img 
    width 14px;
    margin-top 14px;
</style>

<script>
import Logo from "../../../assets/header/分组.png";
import SerchBtn1 from "../../../assets/header/搜索@2x.png";
import headers from "../../../assets/header/bc8cbb0.gif";
export default {
  data(){
    return {
      hasLog:true,
      logo:Logo,
      serchBtn1:SerchBtn1,
      header:headers,
      userName:"潘磊",
      department:"运保部门",
      job:"系统管理员"
    }
  },
  methods:{
    //预警预览点击事件
    showWarning:function(){
      this.hasLog = false;
    }
  }
}
</script>


