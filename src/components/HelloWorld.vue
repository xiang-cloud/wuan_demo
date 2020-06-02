<template>
    <div>
        <Submit @comment="addComment"></Submit>
        <Comment :message="comment"></Comment>
        
       
    </div>
</template>

<script>
import Comment from "@/components/common/Comment"
import Submit from "@/components/common/Submit"
export default {
    name: "HelloWorld",
    data() {
        return {
            msg: "Welcome to Your Vue.js App",
            comment:[]
        };
    },
    components: {
        Comment,
        Submit,
    },
    methods: {
        addComment(data){
            console.log('传递参数到父组件：')
            this.comment = data
            console.log(data)
        }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
