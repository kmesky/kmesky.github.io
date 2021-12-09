/**
* 远程唤醒界面
*/
<template>
  <!-- 组件主盒子 -->
  <div class="stbox">
    <!-- 面包屑导航 -->
    <el-breadcrumb separator-class="el-icon-arrow-right">
      <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
      <el-breadcrumb-item>远程唤醒</el-breadcrumb-item>
    </el-breadcrumb>
    <el-form :inline="true" :model="wakeForm" class="wake-form">
      <el-form-item label="IP">
        <el-input size="small" v-model="wakeForm.ip" placeholder="IP或域名"></el-input>
      </el-form-item>
      <el-form-item label="MAC">
        <el-input size="small" v-model="wakeForm.mac" placeholder="MAC地址" auto-complete="off"></el-input>
      </el-form-item>
      <el-form-item label="端口">
        <el-input size="small" v-model="wakeForm.port" placeholder="端口号"></el-input>
      </el-form-item>
      <el-form-item>
<!--        <el-button size="small" type="primary" icon="el-icon-search" @click="search">搜索</el-button>-->
<!--        <el-button size="small" type="primary" icon="el-icon-plus" @click="handleEdit()">添加</el-button>-->
        <el-button size="small" type="primary" @click="submitForm('wakeForm')" :loading="logining">唤醒
        </el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
<script type="text/ecmascript-6">
import Chart from 'echarts'

export default {
  name: "welcome",
  data() {
    return {
      //定义loading默认为false
      logining: false,
      // 远程唤醒表单
      wakeForm: {
        ip: '127.0.0.1',
        mac: '0A-1B-2C-3D-4E-5F',
        port: '1111',
      },
      formInline: {
        page: 1,
        limit: 10,
        varLable: '',
        varName: '',
        token: localStorage.getItem('logintoken')
      },
    }
  },
  // 导入组件
  components: {
    // 点聚合组件
  },
  // 创建完毕状态(里面是操作)
  created() {
    this.mac = '0A-1B-2C-3D-4E-5F'
  },
  // 挂载结束状态(里面是操作)
  mounted() {
    this.getSCE()
    this.getSUM()
    this.getClick()
    this.getpay()
    this.getpayNum()
  },
  // 里面的函数只有调用才会执行
  methods: {
    submitForm(formName) {

    },
    // 交易总笔数
    getSCE() {
      this.chart = Chart.init(this.$refs.SCEchart)
      this.chart.setOption(this.SCEoption)
    },
    // 交易总金额
    getSUM() {
      this.chart = Chart.init(this.$refs.SUMEchart)
      this.chart.setOption(this.SUMoption)
    },
    // 总点击量
    getClick() {
      this.chart = Chart.init(this.$refs.ClickEchart)
      this.chart.setOption(this.Clickoption)
    },
    // 支付方式统计
    getpay() {
      this.chart = Chart.init(this.$refs.payEchart)
      this.chart.setOption(this.payoption)
    },
    // 支付方式统计
    getpayNum() {
      this.chart = Chart.init(this.$refs.payNumEchart)
      this.chart.setOption(this.payNumoption)
    }

  }
};
</script>
<style>
.stbox {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
}

.stbgc {
  background-color: #fff;
  height: 60px;
  line-height: 60px;
  border-radius: 5px;
  padding: 0px 16px;
}

.stsearch {
  text-align: center;
}
.wake-form {
  margin-top: 20px;
  /*text-align: left;*/
}

.text-c {
  text-align: center;
}

.st-gbox {
  background-color: #fff;
  margin-top: 20px;
  border-radius: 5px;
  height: 30vh;
  box-sizing: border-box;
  padding: 10px;
}

.cavasbox {
  box-sizing: border-box;
  width: 100%;
  height: 100%;
}

.paybox {
  width: 100%;
  background-color: #fff;
  box-sizing: border-box;
  border-radius: 5px;
  margin-top: 20px;
  height: 32vh;
}
</style>
