<template>
  <div class="form-print-page">
    <div class="flex-row title">
      <span class="edit-box">佛山市</span>
      <h2>医疗保障基金结算清单</h2>
    </div>
    <div class="flex-row flex-end">
      <div class="col-item">
        <div>定点医疗机构名称 _______</div>
        <div>医保编号___________</div>
      </div>
      <div class="col-item">
        <div>定点医疗机构代码________</div>
        <div>病案号______</div>
      </div>
      <div class="col-item date-box">
        <div>清单流水号__________</div>
        <div>医保结算等级__________</div>
        <div>申报时间______年____月____日</div>
      </div>
    </div>
    <div class="print-form">
      <div class="form-head">一、基本信息</div>
      <div class="flex-row">
        <div class="print-form-item">姓名__________</div>
        <div class="print-form-item">性别 1.男 2女</div>
        <div class="print-form-item date-box">出生日期____年___月___日</div>
        <div class="print-form-item date-box">年龄____岁</div>
        <div class="print-form-item date-box">国籍______</div>
      </div>
      <div class="flex-row">
        <div class="print-form-item">（年龄不足1周岁）年龄____天</div>
        <div class="print-form-item date-box">民族______</div>
        <div class="print-form-item date-box">患者证件类别____________</div>
        <div class="print-form-item date-box">患者证件号码__________________</div>
      </div>
      <div class="flex-row">
        <div class="print-form-item">职业__________</div>
        <div
          class="print-form-item date-box"
        >现住址______省(区、市)______市______县____________________________</div>
      </div>
      <div class="flex-row">
        <div class="print-form-item">工作单位名称_________________</div>
        <div class="print-form-item date-box">工作单位地址_____________________</div>
        <div class="print-form-item date-box">单位电话___________</div>
        <div class="print-form-item date-box">邮编_________</div>
      </div>
      <div class="flex-row">
        <div class="print-form-item">联系人姓名___________</div>
        <div class="print-form-item date-box">关系______</div>
        <div class="print-form-item date-box">地址______省(区、市)______市______县_______________</div>
        <div class="print-form-item date-box">电话_________</div>
      </div>
      <div class="form-head border-top mt-15">二、门诊慢特病诊疗信息</div>
      <div class="flex-row flex-between print-form-item">
        <div>诊断科别____________</div>
        <div>就诊日期____________</div>
      </div>
      <div class="el-table-box">
        <el-table border :data="sickData" style="width: 100%">
          <el-table-column prop="name" label="诊断名称"></el-table-column>
          <el-table-column prop="code" label="诊断代码"></el-table-column>
          <el-table-column prop="operationName" label="手术及操作名称"></el-table-column>
          <el-table-column prop="operationCode" label="手术及操作代码"></el-table-column>
        </el-table>
      </div>
      <div class="form-head border-top mt-15">三、住院诊疗信息</div>
      <div class="flex-row border-bottom">
        <div class="print-form-item">
          住院医疗
          <span>1.住院</span>
          <span>2.日间手术</span>
        </div>
      </div>
      <div class="flex-row border-bottom">
        <div class="print-form-item">
          入院途径
          <span>1.急诊</span>
          <span>2.门诊</span>
          <span>3.其它医疗机构转入</span>
          <span>9.其他</span>
        </div>
      </div>
      <div class="flex-row border-bottom">
        <div class="print-form-item">
          治疗类别
          <span>1.西医</span>
          <span>
            2.中医(2.1中医)
            <span>2.2民族医</span>
          </span>
          <span>3.中西医</span>
        </div>
      </div>
      <div class="flex-row border-bottom flex-between">
        <div class="print-form-item">入院时间____年___月___日</div>
        <div class="print-form-item">入院类别_______</div>
        <div class="print-form-item">转科类别_______</div>
      </div>
      <div class="flex-row border-bottom flex-between">
        <div class="print-form-item">出院时间____年___月___日</div>
        <div class="print-form-item">出院类别_______</div>
        <div class="print-form-item">实际住院_____天</div>
      </div>
      <div class="flex-row">
        <div class="print-form-item">门（急）诊诊断（西医诊断）________</div>
        <div class="print-form-item">疾病代码________</div>
      </div>
      <div class="flex-row">
        <div class="print-form-item">门（急）诊诊断（中医诊断）________</div>
        <div class="print-form-item">疾病代码________</div>
      </div>
      <div class="el-table-box">
        <el-table border :data="hospitalMsg" style="width: 100%">
          <el-table-column prop="westMsg" label="出院西医诊断"></el-table-column>
          <el-table-column prop="illnessCode1" label="疾病代码"></el-table-column>
          <el-table-column prop="msg1" label="入院病情"></el-table-column>
          <el-table-column prop="chineseMsg" label="出院中医诊断"></el-table-column>
          <el-table-column prop="illnessCode2" label=" 疾病代码"></el-table-column>
          <el-table-column prop="msg2" label="入院病情"></el-table-column>
        </el-table>
      </div>
      <div class="flex-row border-top">
        <div class="print-form-item">诊断代码技术________</div>
      </div>
      <div class="el-table-box">
        <el-table border :data="operationData" style="width: 100%">
          <el-table-column prop="name" label="手术及操作名称" width="200px"></el-table-column>
          <el-table-column prop="code" label="手术及操作代码" width="120px"></el-table-column>
          <el-table-column prop="date" label="手术及操作日期"></el-table-column>
          <el-table-column prop="type" label="麻醉方式"></el-table-column>
          <el-table-column prop="username" label=" 术者医师姓名"></el-table-column>
          <el-table-column prop="userCode" label="术者医师代码"></el-table-column>
          <el-table-column prop="operatorName" label="麻醉医师姓名"></el-table-column>
          <el-table-column prop="operatorCode" label="麻醉医师代码"></el-table-column>
        </el-table>
      </div>
      <div class="flex-row border-top">
        <div class="print-form-item">手术及操作代码计数________</div>
      </div>
      <div class="flex-row border-top">
        <div class="print-form-item">呼吸机使用时间____天___小时___分钟</div>
      </div>
      <div class="flex-row border-top">
        <div class="print-form-item">颅脑损伤患者昏迷时间：入院前____天___小时___分钟</div>
        <!-- <div class="print-form-item">入院后____天___小时___分钟</div> -->
      </div>
      <div class="flex-row">
        <span class="empty-box"></span>
        <div class="print-form-item">入院后____天___小时___分钟</div>
      </div>
      <div class="el-table-box">
        <el-table border :data="icuData" style="width: 100%">
          <el-table-column
            prop="type"
            label="重症监护病房类型*（CCU、NICU、EICU、SICU、PICU、RICU、其他）"
            width="300px"
          ></el-table-column>
          <el-table-column prop="inDate" label="进重症监护室时间*（_年_月_日_时_分）"></el-table-column>
          <el-table-column prop="outDate" label=" 出重症监护室时间*（_年_月_日_时_分）"></el-table-column>
          <el-table-column prop="sum" label="合计（小时）*" align="center"></el-table-column>
        </el-table>
      </div>
      <div class="flex-row border-top">
        <div class="print-form-item">输血品种________</div>
        <div class="print-form-item">输血量________</div>
        <div class="print-form-item">输血计量单位________</div>
      </div>
      <div class="flex-row border-top">
        <div class="print-form-item">特级护理天数*________</div>
        <div class="print-form-item">一级护理天数*________</div>
        <div class="print-form-item">二级护理天数*________</div>
        <div class="print-form-item">三级护理天数*________</div>
      </div>
      <div class="flex-row border-top">
        <div class="print-form-item">
          离院方式
          <span>1.医嘱离院</span>
          <span>
            2.医嘱转院，拟接收机构名称____________
            <span>拟接收机构代码____________</span>
          </span>
          <div class="print-form-item pd0">
            <span>
              3.转社区、转卫生院机构，拟接收机构名称__________
              <span>拟接收机构代码________</span>
            </span>
            <span>4.非医嘱离院</span>
            <span>5.死亡</span>
            <span>9.其他</span>
          </div>
        </div>
      </div>
      <div class="flex-row border-top">
        <div class="print-form-item">
          是否有出院31天内再住院计划
          <span>1.无</span>
          <span>1.有，目的_________________</span>
        </div>
      </div>
      <div class="flex-row border-top">
        <div class="print-form-item width-50">主治医师姓名*________</div>
        <div class="print-form-item width-50">
          <span>主治医师代码*________</span>
        </div>
      </div>
      <div class="form-head border-top mt-15">四、医疗收费信息</div>
      <div class="flex-row">
        <div class="width-32 print-form-item">
          <div>业务流水号：____________</div>
          <div>票据代码：____________</div>
          <div>票据代码：____________</div>
        </div>
        <div class="flex-1 print-form-item">
          <div>结算期间：_______年_____月______日——_______年_____月______日</div>
        </div>
      </div>
      <div class="el-table-box">
        <el-table border :data="payData" style="width: 100%">
          <el-table-column prop="name" label="项目名称" align="center" width="283px"></el-table-column>
          <el-table-column prop="price" label="金额" align="center"></el-table-column>
          <el-table-column prop="jia" label="甲类" align="center"></el-table-column>
          <el-table-column prop="yi" label="乙类" align="center"></el-table-column>
          <el-table-column prop="own" label=" 自费" align="center"></el-table-column>
          <el-table-column prop="other" label="其他" align="center"></el-table-column>
        </el-table>
      </div>
      <div class="border-top col-tabl-wrap flex-row">
        <div class="col-title">
          <div>基</div>
          <div>金</div>
          <div>支</div>
          <div>付</div>
        </div>
        <div class="el-table-box">
          <el-table border :data="jijinPayData" style="width: 100%">
            <el-table-column prop="name" label="项目名称" align="center"></el-table-column>
            <el-table-column prop="price" label="金额" align="center"></el-table-column>
          </el-table>
        </div>
        <div class="col-title">
          <div>个</div>
          <div>人</div>
          <div>支</div>
          <div>付</div>
        </div>
        <div class="el-table-box">
          <el-table border :data="jijinPayData" style="width: 100%">
            <el-table-column prop="name" label="项目名称" align="center"></el-table-column>
            <el-table-column prop="price" label="金额" align="center"></el-table-column>
          </el-table>
        </div>
      </div>
      <div class="flex-row border-top">
        <div class="print-form-item">
          医保支付方式
          <span>1.按项目</span>
          <span>2.单病种</span>
          <span>3.按病种分值</span>
          <span>4.疾病诊断相关分组（DRG）</span>
          <span>5.按床日</span>
          <span>6.按人头......</span>
        </div>
      </div>
    </div>
    <div class="form-footer">
      <div class="flex-row">
        <div class="print-form-item">医疗机构填报部门_________</div>
        <div class="print-form-item">医保机构_________</div>
      </div>
      <div class="flex-row">
        <div class="print-form-item">医疗机构填报人_________</div>
        <div class="print-form-item">医保机构经办人_________</div>
      </div>
      <div>（注：“*”代表选填数据项）</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sickData: [
        {
          name: "",
          code: "",
          operationName: "",
          operationCode: "",
        },
        {
          name: "",
          code: "",
          operationName: "",
          operationCode: "",
        },
        {
          name: "",
          code: "",
          operationName: "",
          operationCode: "",
        },
        {
          name: "",
          code: "",
          operationName: "",
          operationCode: "",
        },
      ],
      hospitalMsg: [
        {
          westMsg: "主要诊断：",
          illnessCode1: "",
          msg1: "",
          chineseMsg: "主病：",
          illnessCode2: "",
          msg2: "",
        },
        {
          westMsg: "其他诊断：",
          illnessCode1: "",
          msg1: "",
          chineseMsg: "主症：",
          illnessCode2: "",
          msg2: "",
        },
        {
          westMsg: "",
          illnessCode1: "",
          msg1: "",
          chineseMsg: "",
          illnessCode2: "",
          msg2: "",
        },
        {
          westMsg: "",
          illnessCode1: "",
          msg1: "",
          chineseMsg: "",
          illnessCode2: "",
          msg2: "",
        },
        {
          westMsg: "",
          illnessCode1: "",
          msg1: "",
          chineseMsg: "",
          illnessCode2: "",
          msg2: "",
        },
        {
          westMsg: "",
          illnessCode1: "",
          msg1: "",
          chineseMsg: "",
          illnessCode2: "",
          msg2: "",
        },
      ],
      operationData: [
        {
          name: "主要：",
          code: "",
          date: "",
          type: "",
          username: "",
          userCode: "",
          operatorName: "",
          operatorCode: "",
        },
        {
          name: "其他：",
          code: "",
          date: "",
          type: "",
          username: "",
          userCode: "",
          operatorName: "",
          operatorCode: "",
        },
        {
          name: "",
          code: "",
          date: "",
          type: "",
          username: "",
          userCode: "",
          operatorName: "",
          operatorCode: "",
        },
        {
          name: "",
          code: "",
          date: "",
          type: "",
          username: "",
          userCode: "",
          operatorName: "",
          operatorCode: "",
        },
        {
          name: "",
          code: "",
          date: "",
          type: "",
          username: "",
          userCode: "",
          operatorName: "",
          operatorCode: "",
        },
        {
          name: "",
          code: "",
          date: "",
          type: "",
          username: "",
          userCode: "",
          operatorName: "",
          operatorCode: "",
        },
        {
          name: "",
          code: "",
          date: "",
          type: "",
          username: "",
          userCode: "",
          operatorName: "",
          operatorCode: "",
        },
        {
          name: "",
          code: "",
          date: "",
          type: "",
          username: "",
          userCode: "",
          operatorName: "",
          operatorCode: "",
        },
      ],
      icuData: [
        {
          type: "",
          inDate: "",
          outDate: "",
          sum: "",
        },
        {
          type: "",
          inDate: "",
          outDate: "",
          sum: "",
        },
        {
          type: "",
          inDate: "",
          outDate: "",
          sum: "",
        },
      ],
      payData: [
        { name: "床位费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "诊查费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "检查费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "化验费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "治疗费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "手术费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "护理费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "卫生材料费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "西药费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "中药饮片费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "中药药费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "一般诊疗费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "挂号费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "其他费", price: "", jia: "", yi: "", own: "", other: "" },
        { name: "金额合计", price: "", jia: "", yi: "", own: "", other: "" },
      ],
      jijinPayData: [
        {
          name: "医保统筹基金支付",
          price: "",
        },
        {
          name: "其他支付",
          price: "",
        },
        {
          name: "大病保险",
          price: "",
        },

        {
          name: "医疗救助",
          price: "",
        },
        {
          name: "公务员医疗补助",
          price: "",
        },
        {
          name: "大额补充",
          price: "",
        },
        {
          name: "企业补充",
          price: "",
        },
        {
          name: "",
          price: "",
        },
        {
          name: "",
          price: "",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.form-print-page {
  font-size: 14px;
  width: 842px;
  margin: 0 auto;
  line-height: 24px;
  .title {
    justify-content: center;
  }
  .flex-row {
    display: flex;
    align-items: center;
    .width-50 {
      width: 50%;
      &:nth-child(2) {
        border-left: 1px solid #333;
        span {
          margin-left: 15px;
        }
      }
    }
    .width-32 {
      width: 32%;
      border-right: 1px solid #333;
    }
    .flex-1 {
      flex: 1;
    }
  }
  .flex-between {
    justify-content: space-between;
  }
  .flex-end {
    align-items: flex-end;
  }
  .edit-box {
    border-bottom: 1px solid #000;
    width: 70px;
    display: inline-block;
    text-align: center;
    padding: 5px 10px;
    margin: 0 5px;
  }
  .date-box {
    .edit-box {
      width: 30px;
    }
  }
  .col-item {
    width: 33%;
    line-height: 24px;
  }
  .empty-box {
    width: 155px;
  }
  .print-form {
    border: 1px solid #333;
    margin-top: 30px;
    .border-top {
      border-top: 1px solid #333;
    }
    .border-bottom {
      border-bottom: 1px solid #333;
    }

    .form-head {
      padding: 10px 0;
      background: #eee;
      color: #333;
      text-align: center;
      border-bottom: 1px solid #333;
    }
    .print-form-item {
      margin: 0 15px;
      padding: 10px 0;
      span {
        margin-right: 20px;
      }
    }
    .pd0 {
      padding-left: 0;
      margin: 0;
    }
  }
  .col-tabl-wrap {
    .col-title {
      width: 50px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }
    .el-table-box {
      width: 45%;
    }
  }
  .form-footer {
    padding: 15px;
    .print-form-item {
      width: 45%;
    }
  }
}
// 重写样式
::v-deep .el-table-box .el-table td,
.el-table th.is-leaf,
::v-deep .el-table-box .el-table--border td,
.el-table--border th,
.el-table--border td,
.el-table--border th,
::v-deep
  .el-table-box
  .el-table__body-wrapper
  .el-table--border.is-scrolling-left
  ~ .el-table__fixed,
.el-table td,
::v-deep .el-table-box .el-table th.is-leaf {
  border-bottom: 1px solid #333;
  border-right: 1px solid #333;
}
::v-deep .el-table-box .el-table th,
.el-table tr {
  border-top: 1px solid #333;
}
::v-deep .el-table-box .el-table th,
::v-deep .el-table-box .el-table td {
  padding: 5px 0;
  color: #333;
  height: 30px;
}
</style>