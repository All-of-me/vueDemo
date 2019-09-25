<template>
    
        <div class="a">
            <p>{{comment.name}}说：</p>
            <p class="small-size">{{comment.pinglun}}</p>
            <div class="del">
                <input type="button" @click="delItem" value="删除">
            </div>               
        </div>
</template>
<script>
export default {
    props:{  //指定属性名和属性值的类型 
        comment:Object,
        index:Number,
        del:Function
    },
    methods:{
        delItem(){
            const {comment,index,del} = this
            if(window.confirm('`确定删除${comment.name}的评论吗？`')){
                del(index)
            }
        }
    }
}
</script>
<style>

.small-size{
    text-indent:2em;
    font-size:12px;
}
.del{
    height:15px;
    width:30px;
    position:relative;
    top:-70px;
    right:-600px;
}
p{
    width:80%;
    left:5px;
}
.a{
    padding-left:10px;
    padding-bottom:10px;
    margin:10px;
    width:95%;
    height:80px;
    border:1px solid rgb(231, 225, 225) ;
}
</style>
