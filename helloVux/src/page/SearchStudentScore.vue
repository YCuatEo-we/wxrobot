<template>
  <div>
    <search @result-click="resultClick" @on-change="getResult" :results="results" v-model="value" position="absolute" auto-scroll-to-top top="46px" @on-focus="onFocus" @on-cancel="onCancel"></search>
  </div>
</template>

<script>
  import { Search, Group, Cell } from 'vux'

  export default {
    components: {
      Search,
      Group,
      Cell
    },
    created: function () {
    },
    methods: {
      resultClick (item) {
        window.alert('you click the result item: ' + JSON.stringify(item))
      },
      getResult (val) {
        this.results = val ? getResult(this.value) : []
      },
      onFocus () {
        console.log('on focus')
      },
      onCancel () {
        console.log('on cancel')
      }
    },
    data () {
      return {
        results: [],
        value: 'test'
      }
    }
  }

  function getResult (val) {
    let rs = []
    for (let i = 0; i < 8; i++) {
      rs.push({
        title: `${val} result: ${i + 1} `,
        other: i
      })
    }
    return rs
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
