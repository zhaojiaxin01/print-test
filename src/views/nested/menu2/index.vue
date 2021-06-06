<template>
  <div class="form-print-page">
    <div class="flex-row"><span class="edit-box">佛山市</span><h2>医疗保障基金结算清单</h2></div>
    <div class="flex-row">
      <div class="col-item">
          <div>定点医疗机构名称<span class="edit-box"></span></div>
          <div>医保编号<span class="edit-box"></span></div>
      </div>  
       <div class="col-item">
          <div>定点医疗机构代码<span class="edit-box"></span></div>
          <div>病案号<span class="edit-box"></span></div>
      </div>  
       <div class="col-item date-box">
          <div>清单流水号<span class="edit-box"></span></div>
          <div>医保结算等级<span class="edit-box"></span></div>
           <div>申报时间<span class="edit-box"></span>年<span class="edit-box"></span>月<span class="edit-box"></span>日</div>
      </div>  
    </div>
  </div>    
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.form-print-page{
  font-size:14px;
  width:100%;
  .flex-row{
    display:flex;
    align-items:center;
  }
  .edit-box{
    border-bottom:1px solid #000;
    width:70px;
    display: inline-block;
    text-align:center;
    padding:5px 10px;
    margin:0 5px;
  }
  .date-box{
    .edit-box{
      width:30px;
    }
  }
  .col-item{
    width:20%;
    line-height:36px;
  }
}
</style>