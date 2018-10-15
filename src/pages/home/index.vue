<template>
    <div class="home">
       <!--pages/page/home/home.wxml-->
        <div class='container'>
            <!--背景图  -->
            <img src="../../conmon/img/img_bgpic@2x.png" class='top_bgImg' />
            <!--收益  -->
            <div class='earnings_container'>
                <text class='earnings_text1'><text>￥</text>{{number}}</text>
                <text class='earnings_text2'>今日收益</text>
            </div>
            <!--交易笔数 营销 -->
            <div class='deal_marketing'>
                <div>
                    <text class='deal_marketing_text1'>0</text>
                    <text class='deal_marketing_text2'>交易笔数</text>
                </div>
                <div>
                    <text class='deal_marketing_text1' v-if="user_type != 1">-</text>
                    <text class='deal_marketing_text1' v-if="user_type == 1"><text>￥</text>{{Marketing_reward}}</text>
                    <text class='deal_marketing_text2'>营销奖励</text>
                </div>
            </div>
            <!--功能菜单列表  -->
            <div class='list_container'>
                <div class='cell_container' @click="transaction_record_click">
                    <div class='let_icon_text'>
                        <img src="../../conmon/img/icon_record@3x.png" />
                        <text>交易记录</text>
                    </div>
                    <img class='goto_img' src="../../conmon/img/btn_goto@3x.png" />
                </div>
                <!-- <div class='cell_container' @click='revenue_statement_click'>
                    <div class='let_icon_text'>
                        <img src="../../conmon/img/icon_reward@3x.png"/>
                        <text>营收报表</text>
                    </div>
                    <img class='goto_img' src="../../conmon/img/btn_goto@3x.png"/>
                </div> -->
                <div class='cell_container' @click="marketing_reward_click">
                    <div class='let_icon_text'>
                        <img src="../../conmon/img/icon_reward@3x.png" />
                        <text>营销奖励</text>
                    </div>
                    <img class='goto_img' src="../../conmon/img/btn_goto@3x.png" />
                </div>
                <div class='cell_container' @click="order_check_click">
                    <div class='let_icon_text'>
                    <img src="../../conmon/img/icon_check@3x.png" />
                    <text>订单核验</text>
                    </div>
                    <img class='goto_img' src="../../conmon/img/btn_goto@3x.png" />
                </div>   
            </div>
        </div>
    </div>
</template>

<script>
export default {
    async mounted() {
        await this.$wx.login()
        let data =  await this.$wx.getUserInfo()
        this.$store.dispatch('userInfo/setUserInfo', data.userInfo)
        console.log(data)
    },
    data: () => ({
        number:'2'
    }),
    methods:{
        //跳转到交易记录
        transaction_record_click(){
            wx.navigateTo({
                url: '../transaction_record/main',
            })
        },
        //跳转到营销奖励
        marketing_reward_click(){
            wx.navigateTo({
                url: '../marketing_reward/main',
            })
        },
        //跳转到订单核验
        order_check_click(){
            wx.navigateTo({
                url: '../order_check/main',
            })
        },
    }
    
}
</script>

<style lang="scss">
@import '../../conmon/scss/base.scss';
page{
  width: 100%;
  height: 100%;
  padding: 0;
  margin: 0;
}
.container{
  width: 100%;
  height: 100%;
  padding: 0;
  margin: 0;
}
/*背景  */
.top_bgImg{
  width: 100%;
  height: 160px;
}
/*今日收益  */
.earnings_container{
  position: fixed;
  top: 10px;
  width: 100%;
  text-align: center;
  display: flex;
  flex-direction: column;
}
.earnings_text1{
  font-size: 30px;
  color: #ffffff;
}
.earnings_text1 text{
  font-size: 20px;
  color: #ffffff;
}
.earnings_text2{
  margin-top: 5px;
  font-size: 18px;
  color: #ffffff;
}
/*交易 营销 */
.deal_marketing{
  width: 90%;
  height: 85px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  position: fixed;
  top: 100px;
  left: 5%;
  background-color: #ffffff;
  opacity: 0.8;
  border-radius: 5px;
  box-shadow: 0px 1px 3px gainsboro;
}
.deal_marketing view{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.deal_marketing_text1{
  font-size: 25px;
  line-height: 30px;
}
.deal_marketing_text1 text{
  font-size: 20px;
}
.deal_marketing_text2{
  font-size: 14px;
  color: rgb(175, 175, 175);
}
/*功能菜单  */
.list_container{
  margin-top: 28px;
  width: 90%;
  margin-left: 5%;
}
.cell_container{
  height: 80px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid  rgb(245, 245, 245);
}
.let_icon_text{
  display: flex;
  align-items: center;
}
.let_icon_text image{
  width: 50px;
  height: 50px;
}
.let_icon_text text{
  margin-left: 20px;
  font-size: 14px;
}
.goto_img{
  width: 10px;
  height: 10px;
}
</style>
