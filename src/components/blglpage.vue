<template>
<div class="blgl-container">
    <div class="search-row">
        <div class="search-input-item">
            <el-input style="width:300px;margin-right:40px;" v-model="search_obj.pname" placeholder="输入病人名字"></el-input>
        </div>
        <div class="search-range-date-item">
            <el-date-picker
                class="rq-input"
                v-model="rangeDate"
                type="daterange"
                range-separator="至"
                start-placeholder="开始日期"
                end-placeholder="结束日期">
            </el-date-picker>
        </div>
        <div class="search-input-item">
            <el-input style="width:435px;margin-right:40px;" v-model="search_obj.keyWords" placeholder="输入关键字"></el-input>
        </div>
        <div class="search-row-btn-group">
          <el-button class="btn-default btn-deault-size btn-color-blue" @click="getblList">查询</el-button>
        </div>
    </div>
    <div class="table-continer">
        <el-table
        :data="tableData.list"
        ref="table"
        :header-row-class-name="headerClassname"
        :row-class-name="rowClassname"
        stripe
        style="border:1px solid #ebeef5;overflow-y:auto;height:100%;"
        @selection-change="handleSelectionChange">
        <el-table-column
            type="selection"
            width="96">
        </el-table-column>
        <el-table-column
        prop="pName"
        label="姓名"
        width="150">
        </el-table-column>
        <el-table-column
        prop="inquiryDate"
        label="就诊时间"
        width="280">
        </el-table-column>
        <el-table-column
        prop="gender"
        label="性别"
        width="130">
        </el-table-column>
        <el-table-column
        prop="age"
        label="年龄"
        width="130">
        </el-table-column>
        <el-table-column
        prop="residence"
        label="来源地"
        width="300">
        </el-table-column>
        <el-table-column
        label="操作">
       <template slot-scope="scope">
            <el-button @click="delDailyPatient(scope.row)" type="text" class="btn-font-default bnt-font-color">删除病历</el-button>
            <el-button @click="gotoWzxxPage(scope.row)" type="text" class="btn-font-default">查看四诊</el-button>
            <el-button @click="gotoyfpage(scope.row)" type="text" class="btn-font-default">查看病历</el-button>
       </template>
        </el-table-column>
    </el-table>
  </div>

  <div class="foot-container">
      <div class="page-container">
        <el-pagination
        background
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page="tableData.pageNum"
        :page-size="tableData.pageSize"
        layout="total, prev, pager, next, jumper"
        :total="tableData.total">
      </el-pagination>
    </div>
    <div class="search-row-btn-group">
       <el-button class="btn-default btn-deault-size btn-color-blue" @click="exportBlList">导出病历</el-button>
    </div>
  </div>
</div> 
</template>
<style lang="scss">
    // @import "@/assets/css/blglpage.scss"
    @import "../assets/css/blglpage.scss"
</style>

<script src = "../assets/js/blglpage.js">

</script>
