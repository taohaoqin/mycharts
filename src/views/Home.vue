<template>
<div class="thq">
    <MyEcharts :dataNumber="chartData" :dataName="chartName"></MyEcharts>
    <div>
    <el-table :data="tableData" style="width: 100%">
     <el-table-column  type="index" label="序号" width="50"></el-table-column>
     <el-table-column prop="name" label="种类" width="90"></el-table-column>
     <el-table-column prop="number" label="销量" width="100">
         <template slot-scope="scope">
            <el-input class="thq-input"  v-model="scope.row.number"></el-input> 
         </template>
     </el-table-column>
    </el-table>
  <MyForm @submitForm="submitForm"></MyForm>
</div>
</div>
</template>
<script>
import MyEcharts from '@/components/MyEcharts.vue'
import MyForm from '@/components/MyForm.vue'


    export default {
         components: {
    MyEcharts,
    MyForm
  },
     data() {
            return {
                tableData: [
                    {
                        name: '衬衫',
                        number: '5'
                    }, 
                    {
                        name: '羊毛衫',
                        number: '20'
                    }, 
                    {
                        name: '雪纺衫',
                        number: '36'
                    }, 
                    {
                        name: '裤子',
                        number: '10'
                    },
                    {
                        name: '高跟鞋',
                        number: '10'
                    },
                    {
                        name: '袜子',
                        number: '20'
                    },
                ],
            }
        }, 
       computed:{
          chartData(){
            return this.tableData.map(item =>{
              return item.number
            })
          },
          chartName(){
            return this.tableData.map(item =>{
              return item.name
            })
          },
        },
        methods: {
            submitForm(name,number){
                this.tableData.push({'name':name, 'number':number})
            }
        }
    }
</script>
<style>
 .thq{
     display: flex;
     flex-direction:row;
 } 
 .thq-input .el-input__inner {
     border: 0 none;  
     height:30px ;
    }
  .thq .Add{
     height: 45px;
     color: #606266;
     border-bottom: 1px solid #ebeef5;
     font-size: 25px;
     line-height: 45px;
     cursor: pointer;
 } 
</style> 