<template>
  <div>
    <el-button type="primary" size="mini" style="margin: 30px 90px;" v-print="'#print'">点击打印</el-button>
    <div id="print">
      <div class="form-print-page">
        <div class="flex-row title">
          <span class="underline">{{setlinfo.fixmedins_name?setlinfo.fixmedins_name:''}}</span>
          <h2>医疗保障基金结算清单</h2>
        </div>
        <div class="flex-row flex-end">
          <div class="col-item">
            <div>
              定点医疗机构名称：
              <span class="underline">{{setlinfo.fixmedins_name}}</span>
            </div>
            <div>
              医保编号：
              <span class="underline">{{setlinfo.hi_no}}</span>
            </div>
          </div>
          <div class="col-item">
            <div>
              定点医疗机构代码：
              <span class="underline">{{setlinfo.fixmedins_code}}</span>
            </div>
            <div>
              病案号：
              <span class="underline">{{setlinfo.medcasno}}</span>
            </div>
          </div>
          <div class="col-item">
            <div>
              清单流水号：
              <span class="underline">{{selListId}}</span>
            </div>
            <div>
              医保结算等级：
              <span class="underline">{{setlinfo.hi_setl_lv}}</span>
            </div>
            <div>
              申报时间：
              <span class="underline">{{setlinfo.dcla_time}}</span>
            </div>
          </div>
        </div>
        <div class="print-form">
          <div class="form-head">一、基本信息</div>
          <div class="flex-row">
            <div class="print-form-item">
              姓名：
              <span class="underline">{{setlinfo.psn_nam}}</span>
            </div>
            <div class="print-form-item">
              性别：
              <span class="underline">{{setlinfo.gend === 1?'男':'女'}}</span>
            </div>
            <div class="print-form-item">
              出生日期：
              <span class="underline">{{setlinfo.brdy === 1?'男':'女'}}</span>
            </div>
            <div class="print-form-item" v-show="setlinfo.age">
              年龄：
              <span class="underline">{{setlinfo.age}}岁</span>
            </div>
            <div class="print-form-item">
              国籍：
              <span class="underline">{{setlinfo.ntly}}</span>
            </div>
            <div class="print-form-item">
              民族：
              <span class="underline">{{getNaty[setlinfo.naty]}}</span>
            </div>
          </div>
          <div class="flex-row">
            <div class="print-form-item">
              <!-- v-show="setlinfo.nwb_age" -->
              （年龄不足1周岁）年龄：
              <span class="underline">1{{setlinfo.nwb_age}}天</span>
            </div>

            <div class="print-form-item">
              患者证件类别：
              <span class="underline">{{getCertType[setlinfo.patn_cert_type]}}</span>
            </div>
            <div class="print-form-item">
              患者证件号码：
              <span class="underline">{{setlinfo.certno}}</span>
            </div>
          </div>
          <div class="flex-row">
            <div class="print-form-item">
              职业：
              <span class="underline">{{setlinfo.prfs}}</span>
            </div>
            <div class="print-form-item">
              现住址：
              <span class="underline">{{setlinfo.curr_addr}}</span>
            </div>
          </div>
          <div class="flex-row">
            <div class="print-form-item">
              工作单位名称：
              <span class="underline">{{setlinfo.emp_name}}</span>
            </div>
            <div class="print-form-item">
              工作单位地址：
              <span class="underline">{{setlinfo.emp_addr}}</span>
            </div>
            <div class="print-form-item">
              单位电话：
              <span class="underline">{{setlinfo.emp_tel}}</span>
            </div>
            <div class="print-form-item">
              邮编：
              <span class="underline">{{setlinfo.poscode}}</span>
            </div>
          </div>
          <div class="flex-row">
            <div class="print-form-item">
              联系人姓名：
              <span class="underline">{{setlinfo.coner_name}}</span>
            </div>
            <div class="print-form-item">
              关系：
              <span class="underline">{{getRlts[setlinfo.patn_rlts]}}</span>
            </div>
            <div class="print-form-item">
              地址：
              <span class="underline">{{setlinfo.coner_addr}}</span>
            </div>
            <div class="print-form-item">
              电话：
              <span class="underline">{{setlinfo.coner_tel}}</span>
            </div>
          </div>
          <div class="flex-row">
            <div class="print-form-item">
              医保类型：
              <span class="underline">{{getMedinscatType[setlinfo.hi_type]}}</span>
            </div>
            <div class="print-form-item">
              特殊人员类型：
              <span class="underline">{{spectMan[setlinfo.sp_psn_type]}}</span>
            </div>
            <div class="print-form-item">
              参保地：
              <span class="underline">{{setlinfo.insuplc}}</span>
            </div>
          </div>
          <div class="flex-row">
            <div class="print-form-item">
              新生儿入院类型：
              <span class="underline">{{getAdmType[setlinfo.hi_type]}}</span>
            </div>
            <div class="print-form-item">
              新生儿出生体重：
              <span class="underline">{{setlinfo.nwb_bir_wt}}</span>克
            </div>
            <div class="print-form-item">
              新生儿入院体重：
              <span class="underline">{{setlinfo.nwb_adm_wt}}</span>克
            </div>
          </div>
          <div class="form-head border-top mt-15">二、门诊慢特病诊疗信息</div>
          <div class="flex-row flex-between print-form-item">
            <div>
              诊断科别：
              <span class="underline">{{setlinfo.opsp_diag_caty}}</span>
            </div>
            <div>
              就诊日期：
              <span class="underline">{{setlinfo.opsp_mdtrt_date}}</span>
            </div>
          </div>
          <div class="el-table-box">
            <el-table border :data="setlinfo.opspdiseinfo" style="width: 100%">
              <el-table-column prop="diag_name" label="诊断名称"></el-table-column>
              <el-table-column prop="diag_code" label="诊断代码"></el-table-column>
              <el-table-column prop="oprn_oprt_name" label="手术及操作名称"></el-table-column>
              <el-table-column prop="oprn_oprt_code" label="手术及操作代码"></el-table-column>
            </el-table>
          </div>
          <div class="form-head border-top mt-15">三、住院诊疗信息</div>
          <div class="flex-row border-bottom">
            <div class="print-form-item">
              住院医疗:
              <span class="underline">{{setlinfo.ipt_med_type===1?'住院':'日间手术'}}</span>
            </div>
          </div>
          <div class="flex-row border-bottom">
            <div class="print-form-item">
              入院途径:
              <span class="underline">{{getAway[setlinfo.adm_way]}}</span>
            </div>
          </div>
          <div class="flex-row border-bottom">
            <div class="print-form-item">
              治疗类别:
              <span class="underline">{{getTrtType[setlinfo.trt_type]}}</span>
            </div>
          </div>
          <div class="flex-row border-bottom flex-between">
            <div class="print-form-item">
              入院时间:
              <span class="underline">{{setlinfo.adm_time}}</span>
            </div>
            <div class="print-form-item">
              入院类别:
              <span class="underline">{{getCaty[setlinfo.adm_caty]}}</span>
            </div>
            <div class="print-form-item">
              转科类别:
              <span class="underline">{{getText(setlinfo.refldept_dept,'getDept')}}</span>
            </div>
          </div>
          <div class="flex-row border-bottom flex-between">
            <div class="print-form-item">
              出院时间:
              <span class="underline">{{setlinfo.dscg_time}}</span>
            </div>
            <div class="print-form-item">
              出院类别:
              <span class="underline">{{getCaty[setlinfo.dscg_caty]}}</span>
            </div>
            <div class="print-form-item">
              实际住院:
              <span class="underline">{{setlinfo.act_ipt_days}}</span>天
            </div>
          </div>
          <div class="flex-row">
            <div class="print-form-item">
              门（急）诊诊断（西医诊断）:
              <span class="underline">{{setlinfo. otp_wm_dise}}</span>
            </div>
            <div class="print-form-item">
              疾病代码:
              <span class="underline">{{setlinfo. wm_dise_code}}</span>
            </div>
          </div>
          <div class="flex-row">
            <div class="print-form-item">
              门（急）诊诊断（中医诊断）:
              <span class="underline">{{setlinfo. otp_tcm_dise}}</span>
            </div>
            <div class="print-form-item">
              疾病代码:
              <span class="underline">{{setlinfo. tcm_dise_code}}</span>
            </div>
          </div>
          <div class="el-table-box">
            <el-table border :data="setlinfo.diseinfo" style="width: 100%">
              <el-table-column label="住院诊断类型">
                <template slot-scope="scope">{{getDiagType[scope.row.DIAG_TYPE]}}</template>
              </el-table-column>
              <el-table-column prop="DIAG_CODE" label="疾病代码"></el-table-column>
              <el-table-column label="入院病情">
                <template slot-scope="scope">{{getCondType[scope.row.ADM_COND_TYPE]}}</template>
              </el-table-column>
              <!-- <el-table-column prop="chineseMsg" label="出院中医诊断"></el-table-column>
          <el-table-column prop="diag_code_cnt" label="疾病代码"></el-table-column>
              <el-table-column prop="adm_cond_type" label="入院病情"></el-table-column>-->
            </el-table>
          </div>
          <div class="flex-row border-top">
            <div class="print-form-item">
              诊断代码计数:
              <span class="underline">{{setlinfo.diag_code_cnt}}</span>
            </div>
          </div>
          <div class="el-table-box">
            <el-table border :data="setlinfo.oprninfo" style="width: 100%">
              <el-table-column prop="OPRN_OPRT_NAME" label="手术及操作名称" width="200px"></el-table-column>
              <el-table-column prop="OPRN_OPRT_CODE" label="手术及操作代码" width="120px"></el-table-column>
              <el-table-column prop="OPRN_OPRT_DATE" label="手术及操作日期"></el-table-column>
              <el-table-column label="麻醉方式">
                <template slot-scope="scope">{{getText(scope.row.anst_way,'anstWay')}}</template>
              </el-table-column>
              <el-table-column prop="OPER_DR_NAME" label="术者医师姓名"></el-table-column>
              <el-table-column prop="OPER_DR_CODE" label="术者医师代码"></el-table-column>
              <el-table-column prop="ANST_DR_NAME" label="麻醉医师姓名"></el-table-column>
              <el-table-column prop="ANST_DR_CODE" label="麻醉医师代码"></el-table-column>
            </el-table>
          </div>
          <div class="flex-row border-top">
            <div class="print-form-item">
              手术及操作代码计数:
              <span class="underline">{{setlinfo.oprn_oprt_code_cnt}}</span>
            </div>
          </div>
          <div class="flex-row border-top">
            <div class="print-form-item">
              呼吸机使用时间:
              <span class="underline">{{setlinfo.vent_used_dura}}</span>
            </div>
          </div>
          <div class="flex-row border-top">
            <div class="print-form-item">
              颅脑损伤患者昏迷时间：入院前:
              <span class="underline">{{setlinfo.pwcry_bfadm_coma_dura}}</span>
            </div>
            <!-- <div class="print-form-item">入院后____天___小时___分钟</div> -->
          </div>
          <div class="flex-row">
            <span class="empty-box"></span>
            <div class="print-form-item">
              入院后:
              <span class="underline">{{setlinfo.pwcry_afadm_coma_dura}}</span>
            </div>
          </div>
          <div class="el-table-box">
            <el-table border :data="setlinfo.icuinfo" style="width: 100%">
              <el-table-column
                prop="SCS_CUTD_WARD_TYPE"
                label="重症监护病房类型*（CCU、NICU、EICU、SICU、PICU、RICU、其他）"
                width="300px"
              ></el-table-column>
              <el-table-column prop="SCS_CUTD_INPOOL_TIME" label="进重症监护室时间*（_年_月_日_时_分）"></el-table-column>
              <el-table-column prop="SCS_CUTD_EXIT_TIME" label=" 出重症监护室时间*（_年_月_日_时_分）"></el-table-column>
              <el-table-column prop="SCS_CUTD_SUM_DURA" label="合计（小时）*" align="center"></el-table-column>
            </el-table>
          </div>
          <div class="flex-row border-top">
            <div class="print-form-item">
              输血品种:
              <span class="underline">{{setlinfo.bld_cat}}</span>
            </div>
            <div class="print-form-item">
              输血量:
              <span class="underline">{{setlinfo.bld_amt}}</span>
            </div>
            <div class="print-form-item">
              输血计量单位:
              <span class="underline">{{setlinfo.bld_unt}}</span>
            </div>
          </div>
          <div class="flex-row border-top">
            <div class="print-form-item">
              特级护理天数*:
              <span class="underline">{{setlinfo.spga_nurscare_days}}</span>天
            </div>
            <div class="print-form-item">
              一级护理天数*:
              <span class="underline">{{setlinfo.lv1_nurscare_days}}</span>天
            </div>
            <div class="print-form-item">
              二级护理天数*:
              <span class="underline">{{setlinfo.scd_nurscare_days}}</span>天
            </div>
            <div class="print-form-item">
              三级护理天数*:
              <span class="underline">{{setlinfo.lv3_nurscare_days}}</span>天
            </div>
          </div>
          <div class="flex-row border-top">
            <div class="print-form-item">
              离院方式:
              <span class="underline">{{getDesgWay[setlinfo.dscg_way]}}</span>
              <span v-if="setlinfo.dscg_way === 2 || setlinfo.dscg_way === 3">
                拟接收机构名称
                <span class="underline">{{setlinfo.acp_medins_name}}</span>
                <span>
                  拟接收机构代码
                  <span class="underline">{{setlinfo.acp_optins_code}}</span>
                </span>
              </span>
            </div>
          </div>
          <div class="flex-row border-top">
            <div class="print-form-item">
              是否有出院31天内再住院计划:
              <span v-if="setlinfo.days_rinp_flag_31">
                有，目的
                <span class="underline">{{setlinfo.days_rinp_pup_31}}</span>
              </span>
              <span v-else>无</span>
            </div>
          </div>
          <div class="flex-row border-top">
            <div class="print-form-item width-50">
              主治医师姓名*:
              <span class="underline">{{setlinfo.chfpdr_name}}</span>
            </div>
            <div class="print-form-item width-50">
              <span class="ml-15">
                主治医师代码*
                <span class="underline">{{setlinfo.chfpdr_code}}</span>
              </span>
            </div>
          </div>
          <div class="form-head border-top mt-15">四、医疗收费信息</div>
          <div class="flex-row">
            <div class="width-32 print-form-item">
              <div>
                业务流水号：
                <span class="underline">{{setlinfo.biz_sn}}</span>
              </div>
              <div>
                票据代码：
                <span class="underline">{{setlinfo.bill_code}}</span>
              </div>
              <div>
                票据代码：
                <span class="underline">{{setlinfo.bill_no}}</span>
              </div>
            </div>
            <div class="flex-1 print-form-item">
              <div>
                结算期间：
                <span class="underline">{{setlinfo.setl_begn_date}}</span> ——
                <span class="underline">{{setlinfo.setl_end_date}}</span>
              </div>
            </div>
          </div>
          <div class="el-table-box">
            <el-table border :data="setlinfo.iteminfo" style="width: 100%">
              <el-table-column prop="MED_CHRGITM" label="项目名称" align="center" width="283px"></el-table-column>
              <el-table-column prop="AMT" label="金额" align="center"></el-table-column>
              <el-table-column prop="CLAA_SUMFEE" label="甲类" align="center"></el-table-column>
              <el-table-column prop="CLAB_AMT" label="乙类" align="center"></el-table-column>
              <el-table-column prop="FULAMT_OWNPAY_AMT" label=" 自费" align="center"></el-table-column>
              <el-table-column prop="OTH_AMT" label="其他" align="center"></el-table-column>
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
              <div class="fund-box" style="width:100%;">
                <div class="fund-title flex-row">
                  <div>基金支付类型</div>
                  <div>金额</div>
                </div>
                <div class="fund-list">
                  <div
                    class="fund-item flex-row"
                    v-for="(item,index) in setlinfo.payinfo"
                    :key="index"
                  >
                    <div class="tl">{{getText(item.FUND_PAY_TYPE,'fundList')}}</div>
                    <div class="tr">{{item.FUND_PAYAMT}}</div>
                  </div>
                </div>
              </div>
            </div>
            <div class="col-title">
              <div>个</div>
              <div>人</div>
              <div>支</div>
              <div>付</div>
            </div>
            <div class="cell-item-list">
              <div class="cell-item">
                <div class="tl">个人自付</div>
                <div class="tr">{{setlinfo.psn_selfpay}}</div>
              </div>
              <div class="cell-item">
                <div class="tl">个人自费</div>
                <div class="tr">{{setlinfo.psn_ownpay}}</div>
              </div>
              <div class="cell-item">
                <div class="tl">个人账户支付</div>
                <div class="tr">{{setlinfo.acct_pay}}</div>
              </div>
              <div class="cell-item">
                <div class="tl">个人现金支付</div>
                <div class="tr">{{setlinfo.psn_cashpay}}</div>
              </div>
            </div>
          </div>
          <div class="flex-row border-top">
            <div class="print-form-item">
              医保支付方式：
              <span>{{getCashpay[setlinfo.hi_paymtd]}}</span>
            </div>
          </div>
        </div>
        <div class="form-footer">
          <div class="flex-row">
            <div class="print-form-item">
              医疗机构填报部门:
              <span class="underline">{{setlinfo.medins_fill_dept}}</span>
            </div>
            <div class="print-form-item">
              医保机构:
              <span class="underline">{{setlinfo.hsorg}}</span>
            </div>
          </div>
          <div class="flex-row">
            <div class="print-form-item">
              医疗机构填报人:
              <span class="underline">{{setlinfo.medins_fill_psn}}</span>
            </div>
            <div class="print-form-item">
              医保机构经办人:
              <span class="underline">{{setlinfo.hsorg_opter}}</span>
            </div>
          </div>
          <div>（注：“*”代表选填数据项）</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Print from "vue-print-nb";
import Vue from "vue";
Vue.use(Print);
import { setllistCheck } from "@/api/user.js"; // 存放该接口api得文件
import {
  getNaty,
  getAway,
  getTrtType,
  getCaty,
  deptJson,
  getDiagType,
  getCondType,
  anstWay,
  getDesgWay,
  getCashpay,
  getMedinscatType,
  getAdmType,
  fundList,
  getRlts,
  spectMan,
  getCertType,
} from "./getData.js"; // 这个文件存放了数据
export default {
  data() {
    return {
      getNaty,
      getAway,
      getTrtType,
      getCaty,
      deptJson,
      getDiagType,
      getCondType,
      getDesgWay,
      getCashpay,
      getMedinscatType,
      getAdmType,
      getRlts,
      spectMan,
      getCertType,
      setlinfo: {},
      selListId: "",
      fundList,
    };
  },
  created() {
    this.selListId = this.$route.query.selListId;
    // this.initData();
    // 占位符，为了数据表格不变形，
    const { payinfo } = this.setlinfo;
    if (!payinfo) {
      this.setlinfo.payinfo = [];
      for (let i = 0; i < 7; i++) {
        this.setlinfo.payinfo.push({ FUND_PAY_TYPE: "", FUND_PAYAMT: "" });
      }
    } else {
      for (let i = 0; i < 6; i++) {
        this.setlinfo.payinfo.push({ FUND_PAY_TYPE: "", FUND_PAYAMT: "" });
      }
    }
  },
  mounted() {},
  methods: {
    // 数据初始化
    initData() {
      setllistCheck({ selListId: this.selListId }).then((res) => {
        if (res && res.code === 200) {
          this.setlinfo = res.data;
        }
      });
    },
    // 参数code转文字
    getText(code, type) {
      if (code) {
        let items = this[type].filter((item) => {
          if (item.code == code) {
            return item;
          }
        });
        return items && items.length ? items[0].name : "";
      }
    },
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
    font-size: 18px;
    margin-bottom: 30px;
  }
  .el-table-box {
    width: 100%;
    display: block;
  }
  .flex-row {
    display: flex;
    align-items: center;
    .width-50 {
      width: 50%;
      &:nth-child(2) {
        border-left: 1px solid #333;
        .ml-15 {
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
      background: #bad8f7;
      color: #333;
      text-align: center;
      border-bottom: 1px solid #333;
    }
    .print-form-item {
      margin: 0 16px;
      padding: 10px 0;
      span {
        margin-left: 5px;
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
      width: 48%;
    }
  }
  .form-footer {
    padding: 15px;
    .print-form-item {
      width: 45%;
    }
  }
  .underline {
    border-bottom: 1px solid #333;
    min-width: 50px;
    display: inline-block;
    text-align: center;
    height: 24px;
    margin-right: 2px;
  }
}
.cell-item-list {
  flex: 1;
}
.cell-item {
  height: 74px;
  line-height: 74px;
  display: flex;
  align-items: center;
  border-bottom: 1px solid #333;
  border-left: 1px solid #333;
  &:last-child {
    border-bottom: none;
  }
  .tl {
    min-width: 112px;
    text-align: center;
    border-right: 1px solid #333;
  }
  .tr {
    border-left: 1px solid #333;
    padding-left: 20px;
    text-align: center;
    flex: 1;
  }
}
.fund-box {
  border-left: 1px solid #333;
  border-right: 1px solid #333;
  .fund-title,
  .fund-item {
    line-height: 36px;
    width: 100%;
    min-height: 36px;
    text-align: center;
    border-bottom: 1px solid #333;
    &:last-child {
      border: none;
    }
    .tl,
    .tr {
      width: 232px;
      text-align: center;
      min-height: 36px;
      border-right: 1px solid #333;
    }
    .tr {
      flex: 1;
      border-right: none;
    }
  }
  .fund-title {
    div {
      width: 232px;
      border-right: 1px solid #333;
      &:last-child {
        flex: 1;
        border: none;
      }
    }
  }
}
// 重写样式
::v-deep .el-table-box {
  .el-table th.is-leaf,
  .el-table--border td,
  .el-table--border th,
  .el-table--border td,
  .el-table--border th {
    border-bottom: 1px solid #333;
    border-right: 1px solid #333;
  }
  .el-table th,
  .el-table tr {
    border-top: 1px solid #333;
  }
  .el-table td {
    padding: 5px 0;
    color: #333;
    height: 30px;
  }
}
::v-deep .el-table-box {
  .el-table--border {
    border: 1px solid #eee;
  }
}
</style>