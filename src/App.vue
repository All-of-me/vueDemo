<template>
    <div>
        <header class="site-header jumbotron">
            <div class="container">
                请发表对Vue的评论
            </div>
        </header>
            <footer>
                <Add :addComment="addComment"/>
                <List :comments="comments" :del="del"/>
            </footer>
        </div>
</template>
<script>
import Add from './components/Add.vue'
import List from './components/List'
export default {
    data(){
        return{
            // comments:[ //数据在哪个组件，操作数据的方法就应该在哪个组件
            //     {
            //         name:'BOB',
            //         pinglun:'Vue还不错'
            //     },
            //     {
            //         name:'xxx',
            //         pinglun:'Vue有点难'
            //     }
            // ]
            //从localStorage读取comments
            comments:JSON.parse(window.localStorage.getItem('key') || '[]')
        }
    },
    methods:{
        addComment(comment){
            this.comments.unshift(comment)
        },
        del(index){
            this.comments.splice(index,1)
        }
    },

    watch:{ //深度监视
        comments:{
            deep:true, //深度监视
            handler:function(value){
                //将comment最新的值的json数据，保存到localStorage
                window.localStorage.setItem('key',JSON.stringify(value))
            }
        }
    },
    components:{
        Add,
        List 
    }
}
</script>
<style>
body{
    padding:0;
    margin:0;
}
.site-header{
    height: 150px;
    width: 100%;
    background: rgb(233, 229, 229);
    padding-left:268px;
    padding-top:43px;
    font-size:55px;
}




</style>
