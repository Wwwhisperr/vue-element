<template>
  <div class="hello">
    <el-container>
      <el-header>
        <el-row>
          <el-col :span="24">
            <div class="grid-content bg-purple">
              <el-menu
                :default-active="activeIndex"
                class="el-menu-demo"
                mode="horizontal"
                :style="{ backgroundColor: nightbg }"
                :text-color="textColor"
                :active-text-color="atc"
              >
                <!-- @select="handleSelect" -->
                <el-menu-item index="1">处理中心</el-menu-item>
                <el-submenu index="2">
                  <template slot="title">我的工作台</template>
                  <el-menu-item index="2-1">选项1</el-menu-item>
                  <el-menu-item index="2-2">选项2</el-menu-item>
                  <el-menu-item index="2-3">选项3</el-menu-item>
                  <el-submenu index="2-4">
                    <template slot="title">选项4</template>
                    <el-menu-item index="2-4-1">选项1</el-menu-item>
                    <el-menu-item index="2-4-2">选项2</el-menu-item>
                    <el-menu-item index="2-4-3">选项3</el-menu-item>
                  </el-submenu>
                </el-submenu>
                <!-- <el-menu-item index="3" disabled>消息中心</el-menu-item> -->
                <el-menu-item index="4"
                  ><a href="https://www.ele.me" target="_blank"
                    >订单管理</a
                  ></el-menu-item
                >
                <!-- 右侧 -->

                <!-- <el-menu-item index="6" class="right"> -->
                <div class="size-icon right" @click="clickIcon">
                  <i class="el-icon-sunny" v-show="isday"></i>
                  <i class="el-icon-moon" v-show="isnight"></i>
                </div>

                <div class="size-icon right">
                  <el-switch
                    v-model="value"
                    active-text="中文"
                    inactive-text="En"
                  >
                  </el-switch>
                </div>
                <el-avatar
                  :size="40"
                  :src="circleUrl"
                  icon="el-icon-user-solid"
                  class="size-icon right avatar"
                ></el-avatar>
                <!-- </el-menu-item> -->
              </el-menu>
            </div>
          </el-col>
        </el-row>
      </el-header>

      <!-- <el-aside width="200px">Aside</el-aside>
      <el-main>Main</el-main>
      <el-footer>Footer</el-footer> -->
    </el-container>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      value: true,
      isday: true,
      isnight: false,
      activeIndex: "1",
      activeIndex2: "",
      nightbg: "",
      textColor:"",
      atc:"",
      circleUrl: "",
      changeNav: "",
    };
  },
  props: {
    msg: String,
  },
  methods: {
    clickIcon: function () {
      this.isday = !this.isday;
      this.isnight = !this.isnight;
      if (this.isday) {
        this.activeIndex2 = "";
        this.activeIndex = "1";
        this.nightbg = "";
        this.textColor = "";
        this.atc = "";
      }
      if (this.isnight) {
        this.activeIndex = "";
        this.activeIndex2 = "1";
        this.nightbg = "#545c64";
        this.textColor = "#fff";
        this.atc = "#ffd04b";
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* *{
  margin: 0;
  padding: 0;
} */
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.el-header {
  padding: 0;
}
.right {
  float: right;
  margin: 0 20px;
  cursor: pointer;
  line-height: 60px;
  vertical-align: middle;
}
.size-icon {
  font-size: 20px;
}
.avatar {
  margin-top: 10px;
}
</style>
