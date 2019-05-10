<template>
<div>
  <div style="padding: 0px 5%" class="Selection">
    <p class="left">一、UI</p>
    <el-card>
      <div style="float: left">
        <p class="left">WEB、APP 公共</p>
        <div class="button mouse" v-for="item in UIWEBAPP" :key="item.value" @click="Select(item.value)">
          <el-button v-if="stuate.indexOf(item.value) == -1"   circle></el-button>
          <el-button v-else type="warning" icon="el-icon-check"  circle></el-button>&nbsp;&nbsp;<span>{{item.label}}</span>
        </div>
      </div>
      <div class="uiapp">
        <p class="left">APP 特有</p>
        <div class="button mouse" v-for="item in UIAPP" :key="item.value" @click="Select(item.value)">
          <el-button v-if="stuate.indexOf(item.value) == -1"   circle></el-button>
          <el-button v-else type="warning" icon="el-icon-check"  circle></el-button>&nbsp;&nbsp;{{item.label}}
        </div>
      </div>
    </el-card>
    <p class="left">二、交互处理</p>
    <el-card>
      <div style="float: left">
        <p class="left">WEB、APP 公共</p>
        <div class="button mouse" v-for="item in INWEBAPP" :key="item.value" @click="Select(item.value)">
          <el-button v-if="stuate.indexOf(item.value) == -1"   circle></el-button>
          <el-button v-else type="warning" icon="el-icon-check"  circle></el-button>&nbsp;&nbsp;{{item.label}}
        </div>
      </div>
      <div style="float: left">
        <p class="left">APP 特有</p>
        <div class="button mouse" v-for="item in INAPP" :key="item.value" @click="Select(item.value)">
          <el-button v-if="stuate.indexOf(item.value) == -1"   circle></el-button>
          <el-button v-else type="warning" icon="el-icon-check"  circle></el-button>&nbsp;&nbsp;{{item.label}}
        </div>
      </div>
    </el-card>
    <p class="left">三、表单</p>
    <el-card>
      <div class="button mouse" v-for="item in FORM" :key="item.value" @click="Select(item.value)">
      <el-button v-if="stuate.indexOf(item.value) == -1"   circle></el-button>
      <el-button v-else type="warning" icon="el-icon-check"  circle></el-button>&nbsp;&nbsp;{{item.label}}
    </div>
    </el-card>
  </div>
</div>
</template>
<script>
import UrlParse from 'url-parse'
import { UIWEBAPP, UIAPP, INWEBAPP, INAPP, FORM } from '@/data/index.js'
import qs from 'qs'
export default {
  data () {
    return {
      stuate: [],
      UIWEBAPP: [],
      UIAPP: [],
      INWEBAPP: [],
      INAPP: [],
      FORM: []
    }
  },
  created () {
    this.UIWEBAPP = UIWEBAPP
    this.UIAPP = UIAPP
    this.INWEBAPP = INWEBAPP
    this.INAPP = INAPP
    this.FORM = FORM
    const uri = UrlParse(window.location.href)
    const qsObj = qs.parse(uri.query.substr(1))
    if (qsObj.par) {
      this.stuate = JSON.parse(qsObj.par)
    }
  },
  methods: {
    Select (value) {
      if (this.stuate.indexOf(value) === -1) {
        this.stuate.push(value)
      } else {
        var index = this.stuate.indexOf(value)
        this.stuate.splice(index, 1)
      }
      window.location.href = '?par=' + JSON.stringify(this.stuate) + '#/index'
    }
  }
}
</script>
<style scoped>
.left {
  margin-left:30px
}
.mouse {
  cursor: pointer;
  text-decoration: none;
}
.uiapp {
  float: left;
  padding-left: 145px
}
</style>
