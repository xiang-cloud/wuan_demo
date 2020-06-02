<template>
    <div id="submit">
        <el-input v-model="input" placeholder="请输入内容"></el-input>
        <el-button @click="addComment()">默认按钮</el-button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            input: "",
            comment: []
        };
    },
    methods: {
        dateFormat(fmt, date) {
            let ret;
            const opt = {
                "Y+": date.getFullYear().toString(), // 年
                "m+": (date.getMonth() + 1).toString(), // 月
                "d+": date.getDate().toString(), // 日
                "H+": date.getHours().toString(), // 时
                "M+": date.getMinutes().toString(), // 分
                "S+": date.getSeconds().toString() // 秒
                // 有其他格式化字符需求可以继续添加，必须转化成字符串
            };
            for (let k in opt) {
                ret = new RegExp("(" + k + ")").exec(fmt);
                if (ret) {
                    fmt = fmt.replace(
                        ret[1],
                        ret[1].length == 1
                            ? opt[k]
                            : opt[k].padStart(ret[1].length, "0")
                    );
                }
            }
            return fmt;
        },
        addComment() {
            let json = {};
            json.id = "10086";
            json.publisher = "javon";
            json.context = this.input;
            json.created_at = this.dateFormat("YYYY-mm-dd HH:MM", new Date());
            this.input = "";
            this.comment.push(json);
            console.log("json日志为：");
            console.log(json);
            this.$emit("comment", this.comment);
        }
    }
};
</script>

<style>
#submit {
    margin: 0 auto;
    width: 50%;
    padding-top: 20px;
}
.el-input {
    width: 80%;
    float: left;
}
</style>
