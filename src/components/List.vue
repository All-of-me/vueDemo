<template>
    <div class="footer-right common">
        <h3>评论回复：</h3>
        <h2 v-show="comments.length===0">暂无用户评论</h2>
        <div v-show="comments.length!=0" class="list">
            <Item v-for="(comment,index) in comments" :key="index" :comment="comment" :del="del" :index="index"/> 
        </div>
    </div>
</template>
<script>
import Item from './Item.vue'
export default {
    //声明接收属性：这个属性就会成为组件对象的属性
    props:['comments','del'], //只指定属性名
    components:{
        Item
    }
}
</script>
<style>
    .footer-right{
    margin:10px;
    padding-left:10px;
    width:700px;
    height: 350px;
    float:left;
    font-size: 18px;
    color: rgb(105, 103, 103);
}
.list{
    padding:5px;
    width:100%;
    height:300px;
    border:1px solid #999 ;
    overflow:scroll;
}
</style>
