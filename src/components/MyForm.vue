<template>
  <div>
      <div class="Add" @click='toAdd'>+</div> 
    <el-dialog width='20%' :visible.sync="visible" title="添加栏">
   <el-form  ref="tableDataForm"
        :model="tableDataForm"
        :rules="rules"
         label-width="50px">
  <el-form-item label="种类" prop="name">
    <el-input v-model="tableDataForm.name"></el-input>
  </el-form-item>
  <el-form-item label="销量" prop="number">
    <el-input v-model.number="tableDataForm.number"></el-input>
  </el-form-item>
  <el-form-item>
    <el-button type="primary" @click="submitForm('tableDataForm')">确定</el-button>
    <el-button @click="resetForm('tableDataForm')">取消</el-button>
  </el-form-item>
</el-form>
   </el-dialog> 
  </div>
</template>
<script>
export default {
    props: {
    tableData: {
      type: Array,
      default() {
        return []
      }
    }
  },
  data(){
    return{
         visible:false,
         tableDataForm: {
        name: '',
        number: ''
      },
      rules: {
        name: [
          { required: true, message: '请输入商品名称', trigger: 'blur' },
        ],
        number: [
          { required: true, type: 'number', message: '请输入数字', trigger: 'blur' },
        ]
      }   
    }
  },
  watch:{
        visible(){
          this.tableDataForm.name = ''
          this.tableDataForm.number = ''  
    }
  },
  methods:{
        submitForm(formName) {
       this.$refs[formName].validate((valid) => {
        if (valid) {
          this.tableData.push({ name: this.tableDataForm.name, number: this.tableDataForm.number })
          this.visible=false 
        } 
      })
    },
        resetForm(formName){
          this.visible=false      
    },
        toAdd(){
         this.visible=true;
    } 
  }
}
</script>
