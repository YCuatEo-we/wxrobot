<template>
  <div>
    <div class="blur_background">
      <blur :blur-amount=40>
        <p class="center"><img src="../img/xin.jpg"></p>
      </blur>
      <p class="title_desc">今天是<span id="currentDate">{{currentData}}</span>，距离高考还有<span class="diffDate">{{diffDate}}</span>天</p>
    </div>
  <group >
    <cell title="成绩分析" is-link border-intent="false" :arrow-direction="showContent001 ? 'up' : 'down'"  @click.native="showContent001 = !showContent001" >
      <img slot="icon" width="30" style="display:block;margin-right:20px;" src="../img/成绩分析.png">
    </cell>
    <template v-if="showContent001">
      <cell-box :border-intent="false" class="sub-item" is-link>content 001</cell-box>
      <cell-box class="sub-item" is-link>content 001</cell-box>
      <cell-box class="sub-item" is-link>content 001</cell-box>
    </template>

    <cell title='成绩查询' is-link link="/searchStudentScore">
      <img slot="icon" width="30" style="display:block;margin-right:20px;" src="../img/搜索.png">
    </cell>
    <cell title='学校通知' is-link>
      <img slot="icon" width="30" style="display:block;margin-right:20px;" src="../img/发送消息.png">
    </cell>
    <cell title='学生管理' is-link>
      <img slot="icon" width="30" style="display:block;margin-right:20px;" src="../img/设置.png">
    </cell>
  </group>
    <div class="page-tail">
    </div>
  </div>
</template>

<script>
  import { Group, Cell, Blur, CellBox } from 'vux'

  export default {
    components: {
      Group,
      Cell,
      Blur,
      CellBox
    },
    created: function () {
      // `this` 指向 vm 实例
      this.diffDate = diffDays()
      this.currentData = getCurrentDate()
    },
    data () {
      return {
        msg: 'Hello World!',
        diffDate: Number,
        currentDate: Number,
        showContent001: false,
        showContent002: false,
        showContent003: false,
        showContent004: false
      }
    }
  }

  function addZero (obj) {
    if (obj < 10) return '0' + obj
    else return obj
  }

  function getCurrentDate () {
    var myDate = new Date()
    var currYear = myDate.getFullYear()
    var currMonth = myDate.getMonth() + 1
    var currDay = myDate.getDate()
    var monthDate = currYear + '-' + addZero(currMonth) + '-' + addZero(currDay)
    return monthDate
  }

  function diffDays () {
    var beginTime = getCurrentDate()
    var endTime = '2017-06-07'
    var aDate, oDate1, oDate2, days
    aDate = beginTime.split('-')
    oDate1 = new Date(aDate[0], aDate[1], aDate[2])
    aDate = endTime.split('-')
    oDate2 = new Date(aDate[0], aDate[1], aDate[2])
    days = parseInt(Math.abs(oDate1 - oDate2) / 1000 / 60 / 60 / 24)
    return days
  }

</script>

<style scoped>
  .sub-item {
    color: #888;
  }
  .center {
    text-align: center;
    padding-top: 20px;
    color: #fff;
    font-size: 18px;
  }
  .center img {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    border: 4px solid #ececec;
  }
  .title_desc {
    margin-top: 0;
    color: #3a3a3a;
    text-align: center;
    font-size: 16px;
    padding: 0;
  }
  .diffDate {
    font-size: 30px;
    color: red;
  }
  .blur_background {
    background: url(../img/flower.jpg) no-repeat;
    background-size:100%;
  }
</style>
