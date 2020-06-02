<template>
    <div id="comment">
        <div class="block">
            <!-- <span class="demonstration" @click="renderDate()">页数较少时的效果</span> -->
            <el-table
                style="width: 100%;"
                :data="message.slice((currentPage-1)*pagesize,currentPage*pagesize)"
            >
                <el-table-column label="ID3" prop="id" width="200"></el-table-column>
                <el-table-column value-format="yyyy-MM-dd" label="创建自" prop="created_at" width="180"></el-table-column>
                <el-table-column label="用户姓名" prop="publisher" width="180"></el-table-column>
                <el-table-column label="内容" prop="context" width="180"></el-table-column>
                
            </el-table>
            <el-pagination
                @size-change="handleSizeChange"
                @current-change="handleCurrentChange"
                :current-page="currentPage"
                :page-size="pagesize"
                :page-sizes=[1,2,3]       
                layout="total, sizes, prev, pager, next, jumper"
                :total="message.length"
            ></el-pagination>
        </div>
    </div>
</template>

<script>
export default {
    props: ["message"],
    data() {
        return {
            
            currentPage: 1, //初始页
            pagesize: 3 //    每页的数据
        };
    },
    methods: {
        // 初始页currentPage、初始每页数据数pagesize和数据data
        handleSizeChange: function (size) {
                this.pagesize = size;
                
        },
        handleCurrentChange: function(currentPage){
                this.currentPage = currentPage;
        },
    },
    beforeUpdate(){
        let data = {
            currentPage: this.currentPage, //初始页
            pagesize: this.pagesize //    每页的数据
        }
        console.log(data)
    }
};
</script>

<style>
#comment {
    width: 90%;
    height: 300px;
    margin: 0 auto;
    border: 1px solid #000000;
}
</style>
