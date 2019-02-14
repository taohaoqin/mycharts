<template>
  <div>
      <div class="Add" @click='toAdd'>+</div> 
    <el-dialog width='20%' :visible.sync="visible" title="添加栏">
   <el-form  label-width="50px">
  <el-form-item label="种类">
    <el-input  v-model="name"></el-input>
  </el-form-item>
  <el-form-item label="销量" >
    <el-input  v-model="number"></el-input>
  </el-form-item>
  <el-form-item>
    <el-button type="primary" @click="submitForm">确定</el-button>
    <el-button @click="resetForm">取消</el-button>
  </el-form-item>
</el-form>
   </el-dialog> 
  </div>
</template>
<script>
export default {
  data(){
    return{
         visible:false,
         name:'',
         number:'',   
    }
  },
  watch:{
        visible(){
          this.name = ''
          this.number = ''  
    }
  },
  methods:{
       submitForm(){
         if(this.name === "" || /^\d+$/.test(this.name)){//名称不能纯数字或空
           alert('请输入正确的名称')
         } else if(this.number === ""){//销量不能为空
            alert('请输入销量')
         } else if(!/^\d+$/.test(this.number)){//销量只能是数字
           alert('销量框只能输入数字')
         }else{
          this.$emit('submitForm',this.name, this.number)     
         this.resetForm()
         }
    },
        resetForm(){
          this.visible=false      
    },
        toAdd(){
         this.visible=true;
    } 
  }
}
</script>
<style>
.Add{
     height: 45px;
     color: #606266;
     border-bottom: 1px solid #ebeef5;
     font-size: 25px;
     line-height: 45px;
     cursor: pointer;
 } 
</style>
