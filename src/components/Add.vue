<template>
    <div class="footer-left common">
        <div class="name">
            <p>用户名</p>
            <input type="text" id="userName" name="userName" v-model="name" placeholder="用户名" style="width:300px;height:30px"/>
        </div>
                
        <div class="judge">
            <p>评论内容</p>
            <textarea id="pinglun" name="pinglun" v-model="pinglun" placeholder="评论内容" style="width:300px;height:130px;"></textarea>
        </div>
        <div class="sub">
            <input type="button" @click="sub" value="提交">
        </div>
    </div>
</template>
<script>
export default {
    props:{
        addComment:{ //指定属性名、属性值的类型、必要性
            type:Function,
            required:true
        }
    }, 
    data(){
        return {
            name:'',
            pinglun:''
        }
    },
    methods:{
        sub(){
            //1.检查输入的合法性
            const name = this.name.trim()
            const pinglun = this.pinglun.trim()
            if(!name || !pinglun){
                alert('姓名或内容不能为空')
                return
            }
            //2.根据输入的数据，封装成一个comment对象
            const comment = {name,pinglun}

            //3.添加到comments中
            this.addComment(comment)
            //4.清除输入
            this.name=''
            this.pinglun=''
        }   
    }
}
</script>
<style>
.footer-left{
    width:620px;
    height: 400px;
    float:left;
    font-size: 20px;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    color: black;
}
.name{
    height:100px;
    width:170px;
    position:relative;
    top:20px;
    right:-270px;
}
.judge{
    height:150px;
    width:170px;
    position:relative;
    top:20px;
    right:-270px;
}
.sub{
    height:15px;
    width:30px;
    position:relative;
    top:80px;
    right:-530px;
}
textarea{
    resize:none;
}
</style>
