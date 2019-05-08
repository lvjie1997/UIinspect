<template>
<div>
  <div style="padding: 0px 10%" class="Selection">
    <p style="margin-left:30px">一、UI</p>
    <p style="margin-left:30px">WEB、APP 公共</p>
    <div v-for="item in UIWEBAPP" :key="item.value">
      <el-button v-if="stuate.indexOf(item.value) == -1" class="iconempty"  circle @click="Select(item.value)"></el-button>
      <el-button v-else type="warning" icon="el-icon-check"  circle @click="Select(item.value)"></el-button>&nbsp;&nbsp;{{item.label}}<br><br>
    </div>
    <p style="margin-left:30px">APP 特有</p>
    <div v-for="item in UIAPP" :key="item.value">
      <el-button v-if="stuate.indexOf(item.value) == -1" class="iconempty"  circle @click="Select(item.value)"></el-button>
      <el-button v-else type="warning" icon="el-icon-check"  circle @click="Select(item.value)"></el-button>&nbsp;&nbsp;{{item.label}}<br><br>
    </div>
    <p style="margin-left:30px">二、交互处理</p>
    <p style="margin-left:30px">WEB、APP 公共</p>
    <div v-for="item in INWEBAPP" :key="item.value">
      <el-button v-if="stuate.indexOf(item.value) == -1" class="iconempty"  circle @click="Select(item.value)"></el-button>
      <el-button v-else type="warning" icon="el-icon-check"  circle @click="Select(item.value)"></el-button>&nbsp;&nbsp;{{item.label}}<br><br>
    </div>
    <p style="margin-left:30px">APP 特有</p>
    <div v-for="item in INAPP" :key="item.value">
      <el-button v-if="stuate.indexOf(item.value) == -1" class="iconempty"  circle @click="Select(item.value)"></el-button>
      <el-button v-else type="warning" icon="el-icon-check"  circle @click="Select(item.value)"></el-button>&nbsp;&nbsp;{{item.label}}<br><br>
    </div>
    <p style="margin-left:30px">三、表单</p>
    <div v-for="item in FORM" :key="item.value">
      <el-button v-if="stuate.indexOf(item.value) == -1" class="iconempty"  circle @click="Select(item.value)"></el-button>
      <el-button v-else type="warning" icon="el-icon-check"  circle @click="Select(item.value)"></el-button>&nbsp;&nbsp;{{item.label}}<br><br>
    </div>
  </div>
</div>
</template>
<script>
import UrlParse from 'url-parse'
import qs from 'qs'
export default {
  data () {
    return {
      stuate: [],
      UIWEBAPP: [
        {
          value: 1,
          label: '1:是否按照高保真还原，检查位置、边框、边距、对齐、背景、字体大小、透明度、icon等'
        },
        {
          value: 2,
          label: '2:是否处理了没有数据的情况，显示暂无数据 + [图标]'
        },
        {
          value: 3,
          label: '3:是否处理了字符超长，…省略显示，或者自动换行'
        },
        {
          value: 4,
          label: '4:是否做了时间显示格式的统一处理'
        },
        {
          value: 5,
          label: '5:是否做了货币类型格式的统一处理'
        },
        {
          value: 6,
          label: '6:是否做了浮点型数据的精度处理，保留几位小数点'
        },
        {
          value: 7,
          label: '7:是否做了国际化'
        }
      ],
      UIAPP: [
        {
          value: 8,
          label: '8:是否检查过安卓、iOS差异'
        },
        {
          value: 9,
          label: '9:是否做了iOS刘海屏兼容处理'
        },
        {
          value: 10,
          label: '10:是否处理了顶部状态栏的显示'
        },
        {
          value: 11,
          label: '11:是否正确设置了图片上传压缩比例'
        }
      ],
      INWEBAPP: [
        {
          value: 12,
          label: '13:是否在获取列表数据时，显示组件默认的loading状态'
        },
        {
          value: 13,
          label: '13:是否在加载更多列表数据时，显示加载中，没有更多数据时，显示我是有底线的'
        },
        {
          value: 14,
          label: '14:是否在获取非列表数据时，显示我们自定义统一风格的全屏loading状态'
        },
        {
          value: 15,
          label: '15:是否在获取数据成功时，解锁loading状态'
        },
        {
          value: 16,
          label: '16:是否在获取数据失败时，解锁loading状态，并吐司显示错误（通常这里有统一处理）'
        },
        {
          value: 17,
          label: '17:是否对操作类型的按钮做了防抖动处理'
        },
        {
          value: 18,
          label: '18:是否对操作类型的按钮按下动作做了loading与disable状态处理，操作完成，解除loading与disabled状态'
        },
        {
          value: 19,
          label: '19:是否对操作类型的按钮做了再次确认，比如确认、删除的alert警告'
        },
        {
          value: 20,
          label: '20:是否考虑到了UI平滑过度，比如渲染闪烁现象，因为请求前为空，需要考虑初始状态，通常是用loading解决'
        },
        {
          value: 21,
          label: '21:是否处理了表单页面键盘遮挡的问题'
        },
        {
          value: 22,
          label: '22:是否正确设置了弹出框行为，包括弹出方向、速度、关闭等'
        },
        {
          value: 23,
          label: '23:是否处理了菜单、tab、链接已点击或者已激活状态的显示'
        },
        {
          value: 24,
          label: '24:是否考虑了弹出框误点关闭'
        },
        {
          value: 25,
          label: '25:是否处理了选择框跳转二级界面，选择完回填问题'
        },
        {
          value: 26,
          label: '26:是否检查提示消息合理正确'
        }
      ],
      INAPP: [
        {
          value: 27,
          label: '27:是否处理了键盘自动收回'
        },
        {
          value: 28,
          label: '28:是否设置了正确的键盘类型，比如数字、字母'
        },
        {
          value: 29,
          label: '29:是否考虑了异常情况，比如，网络异常、弱网、操作被中断等'
        },
        {
          value: 30,
          label: '30:是否考虑了某些页面不需要物理按键返回或者侧滑返回'
        },
        {
          value: 31,
          label: '31:是否考虑了连续两次物理按钮返回提示退出应用提醒'
        },
        {
          value: 32,
          label: '32:是否考虑了正常的页面返回状态处理，包括路由栈正确弹出，数据重新渲染等'
        },
        {
          value: 33,
          label: '33:是否检查系统推送信息正常处理，点击跳转'
        }
      ],
      FORM: [
        {
          value: 34,
          label: '34: 是否设置了正确的表单类型，比如：邮件、电话、密码、URL、时间等，并做了校验'
        },
        {
          value: 35,
          label: '35:是否设置了文本类型表单最大最小长度'
        },
        {
          value: 36,
          label: '36:是否设置了数字类型表单最大最小值'
        },
        {
          value: 37,
          label: '37:是否设置了必填与非必填字段'
        },
        {
          value: 38,
          label: '38:是否考虑到了表单联动的处理'
        },
        {
          value: 39,
          label: '39:是否做了表单验证'
        },
        {
          value: 40,
          label: '40:是否处理了表单前后空格，trim掉'
        },
        {
          value: 41,
          label: '41:是是否处理了表单填写错误信息提示'
        },
        {
          value: 42,
          label: '42:是否加了placeholder提示'
        },
        {
          value: 43,
          label: '43:是否做了默认值处理'
        }
      ]
    }
  },
  created () {
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
.iconempty {
  height: 20px;
  width: 20px;
}
.mouse {
  cursor: pointer;
  text-decoration: none;
}
</style>
