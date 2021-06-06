<template>
  <div class="form-print-page">
    <div class="flex-row edit-box">佛山市<h2>医疗保障基金结算清单</h2></div>
    <div class="row">
      <div class="col-item">
        <div>
          <span>定点医疗机构名称</span><span class="edit-box"></span>
          <span>医保编号</span><span class="edit-box"></span>
        </div>  
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
  .flex-row{
    display:flex;
    align-items:center;
  }
  .edit-box{
    border-bottom:1px solid #000;
    min-width:100px;
  }
  .col-item{
    width:33%;
  }
}
</style>