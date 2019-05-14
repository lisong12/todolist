<template>
  <div class="todo">
    <!--start todolist-->
    <div class="all">
      <!--添加数据-->
      <div class="nav">
        <input type="text" id="add_list" v-model="text" @keyup.13="add()" name="add_list" placeholder="添加新闻" required>
        <button id="add" @click="add()">添加</button>
      </div>

      <!--显示数据-->
      <div class="text">
        <ol id="todolist" >
          <!--操作数组操作数组 (item,index)-->
          <li v-for="(item,index) in todolist" track-by = "$index" >
            <p :title="item.value">{{item.value}}</p>
            <span @click="del(index)" >删除</span>
          </li>
        </ol>
      </div>

      <!--全部清除-->
      <div class="last">
        <button id="clearbutton"  @click="remove()">清空列表</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default{
    name:'hello',
    data(){
      return{
        todolist:[],//数组
        text:'',   //文本
        state:true, //状态
      }
    },
    methods:{
      //添加
      add(){
        if(this.text == ''){
          return alert("请输入内容！");
        }else{
          this.todolist.push({
            value:this.text,
            state:true,
          })
        }
        this.text='';//清空文本框
      },
      //删除
      del(index){
        this.todolist.splice(index,1);
      },
      //删除所有
      remove(){
        this.todolist = this.todolist.filter(index => !index.state);

      },
    },
  }
</script>
<style>
  .all{
    border: 2px solid blue;
    margin: 0 auto;
    text-align:center;
    width: 40%;
    height: 500px;
    padding: 10px;

  }
  .nav{
    display: flex;
    flex-flow:row nowrap;
    position: relative;
    border: 2px solid blue;
    height:  60px;
  }
  #add_list {
    flex-grow:1;
    /*position: absolute;*/
    /*left: 2px;*/
    /*top: 0px;*/
    /*float:left;*/
    /*margin-top:13px;*/
    width: 80%;
    height:25px;
    font-size: 15px;
    text-indent: 10px;
    margin-left: 5px;
  }
  #add{

    /*position: absolute;*/
    /*right:2px;*/
    /*top: 0px;*/
    /*float: right;*/
    /*margin-top: 10px;*/
    /*margin-right: 5px;*/
    font-size: 14px;
    height: 35px;
    width: 50px;
  }
  .text{
    margin-top:10px;
    height:  350px;
    overflow-y:auto;
    border: 2px solid blue;
  }

  .text ol li{
    display: flex;
    flex-flow:row nowrap;
    list-style: none;
    margin:0 10px 10px -20px;
    /*position: relative;*/
    height: 32px;
    line-height: 32px;
    /*border:1px solid red;*/
    /*border-bottom: 1px solid black;*/
    /*text-align:center;*/
    text-indent: 15px;
    text-align: left;
    /*position: relative;*/

  }
  /*.text ol li p:hover{*/
  /*width:auto;*/
  /*!*鼠标移上去时释放overflowd的截取，按照原本样式显示，即换行*!*/
  /*!**弊端是换行还是会改变布局，但稍微比上面不换行直接显示好一点*!*/
  /*!*text-overflow:inherit;*!*/
  /*!*overflow: visible;*!*/
  /*!*white-space: pre-line;!*合并空白符序列，但是保留换行符。*!*!*/

  /*}*/
  ol li  p{
    flex-grow:1;
    color: #000;
    border:1px solid  #000000 ;
    font-size: 14px;
    height:100%;
    margin-top: -2px;
    margin-right: 10px;
    overflow:hidden;/*内容超出后隐藏*/
    white-space:nowrap;/*文本不会换行，文本会在在同一行上继续，直到遇到 <br> 标签为止。*/
    text-overflow:ellipsis;/*超出文本显示喂省略号*/
  }
  ol li span {
    display: block;
    border:1px solid blue ;
    color: red;
    flex-wrap: nowrap;
    /*position: absolute;*/
    /*bottom: 5px;*/
    /*right: 3px;*/
    /*margin-left: 300px;*/
    width: 50px;
    height: 30px;
    text-align: center;
    line-height: 30px;
    font-size: 14px;
    font-weight: bolder;
    cursor: pointer;
  }

  #clearbutton{
    color:black;
    float: right;
    width: 100px;
    height: 60px;
    margin-top:10px;
    text-align: center;
  }
</style>
