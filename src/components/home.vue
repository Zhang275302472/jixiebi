<template>
  <el-row class="container">
    <el-col :span="24" class="topbar-wrap">
      <div class="topbar-log">
        Linux 协会
      </div>
      <div class="topbar-right">
        <div class="topbar-title">
          <span>robotlink@ designer</span>
        </div>
      </div>
    </el-col>
    <el-col :span="24" class="main">
      <aside >
        <div class="menu-toggle" ><!-- prevent 取消事件的默认动作 -->
          Composition
        </div>
        <el-menu
      default-active="">
        <el-submenu v-for="(item,key) in menu" :index="item.index">
        <template slot="title">
          <i class="el-icon-star-off"></i>
          <span>{{item.name}}</span>
        </template>
          <el-menu-item  @click.native="test(list.name)" v-for="(list,key) in item.items" :index="list.index">{{list.name}}</el-menu-item>
        </el-submenu>
    </el-menu>
      </aside>

      <section class="content-container">
      

      </section>
    </el-col>
  </el-row>
</template>

<script >
  export default {
    data() {
       return {
        collapsed: false,
        menu:[
        {
          index:'1',
          name:'Axis 1 (Start block)',
          items:[
          {
            index:'1-1',
            name:'one'
          },
          {
            index:'1-2',
            name:'two'
          }
          ]
        },
        {
          index:'2',
          name:'Axis 2 (Start block)',
          items:[
          {
            index:'2-1',
            name:'on'
          },
          {
            index:'2-2',
            name:'off'
          }
          ]
        },
        {
          index:'3',
          name:'Axis 3 (Start block)',
          items:[
          {
            index:'3-1',
            name:'on'
          },
          {
            index:'3-2',
            name:'off'
          }
          ]
        },
        {
          index:'4',
          name:'Axis 4 (Start block)',
          items:[
          {
            index:'4-1',
            name:'on'
          },
          {
            index:'4-2',
            name:'off'
          }
          ]
        },
        {
          index:'5',
          name:'Axis 5 (Start block)',
          items:[
          {
            index:'5-1',
            name:'on'
          },
          {
            index:'5-2',
            name:'off'
          }
          ]
        },
         {
          index:'6',
          name:'Axis 6 (Start block)',
          items:[
          {
            index:'6-1',
            name:'Left'
          },
          {
            index:'6-2',
            name:'Right'
          }
          ]
        }
        ]
      }
    },
    methods: {
      //折叠导航栏
      test(e){
        if(e == 'one'){
      this.axios.get('api/handshake_cmd').then((response) => {
  console.log(response.data)
      })
        }
      else if(e == 'two'){
           this.axios.get('api/swing_cmd').then((response) => {
  console.log(response.data)
       })
      }else{
        alert('暂未开发')
      }
      }
   }
  }
</script>
<style scoped lang="scss" type="text/css" scoped="">
  .container{
    position: absolute;
    top: 0px; 
    width: 100%;
    height: 100%;

    .topbar-wrap{
      display: flex;
      height: 50px;
      line-height: 50px;
      background: #353d53;

      .topbar-log{
        display:flex;
        justify-content: center;
        align-content: center;
        width: 200px; 
        color: #fd9c27;
        font-size: 22px;

      }

    }

    .topbar-right{
        display: flex;
        justify-content: space-between;
        align-content: center;
        width: 100%;

      .topbar-title{
        font-size: 1.3rem;
        color: #fff;
      }

      .topbar-account{
        white-space: nowrap;

        .el-dropdown{
          color: #fff;
        }
      }
    }

  .main{
      display: flex;
      position: absolute;
      top: 50px;
      bottom: 0px;
      /*使得aside占全屏幕*/
      overflow: hidden;
      background: linear-gradient(#3a425c,#6377a9, #6679ae); /* 标准的语法 */
    }


  aside{
     width: 330px;
    background: #505f84;
    height: 100%;
    overflow: hidden;

     .el-menu{
          width: calc(100% + 20px);
          height: calc(100% - 40px);
          border-radius: 0px;
          font-weight: 500;
          background: #505f84;
          overflow-y: scroll;
        }


     .el-menu-item:hover, .el-submenu .el-menu-item:hover, .el-submenu__title:hover {
        background-color: #7ed2df;
      }
     .menu-toggle {
      margin: 15px 0 5px; 
      text-align: center;
      color: #eee;
      font-weight: bold;
      font-size: 20px;
      height: 30px;
      line-height: 30px;
    }
    }
    .content-container {
      flex: 1;
      overflow: hidden;
      background-image: url('../img/123.png');
      background-size: 110% 100%;
      background-repeat: no-repeat;
    }

  }

</style>
<style type="text/css">

</style>
