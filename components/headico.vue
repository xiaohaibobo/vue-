<template>
  <div>
    <div class="rest-title">
      <div class="restTcont">
        <p>选择项目头像</p>
        <el-row class="logout">
          <el-button class="logoutBtn" @click="logout">退出</el-button>
        </el-row>
      </div>
    </div>
    <div id="ptList">
      <el-checkbox-group v-model="arr" class="check-group" v-for="(d,i) in data" :key="i">
        <div class="icoCont" style="height:40px" @change="fn(i)">
          <el-checkbox :label="d.name" class="ptcont" border></el-checkbox>
          <img class="userico" :src="d.owner.avatar_url" />
        </div>
      </el-checkbox-group>
    </div>
    <div id="footer5">
      <el-row>
        <el-button type="success" @click="after">上一步</el-button>
        <el-button type="success" @click="next">下一步</el-button>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: [],

      src: {}
    };
  },
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ path: "/login" });
    },
    after() {
      this.$router.push({ path: "/timet" });
    },
    next() {
      this.$router.push({ path: "/beizhu" });
    },
    fn(i) {
      this.src = this.data[i].owner.avatar_url;
      // localStorage.setItem("src", this.src);
      this.$store.dispatch("saveSrc", this.src);
      console.log(this.src);
    }
  },
  computed: {
    data() {
      return this.$store.state.data;
    }
  }

  // watch: {
  //   arr: {
  //     handler() {
  //       this.arr5 = this.arr[0];
  //       localStorage.setItem("arr5", this.arr5);
  //       console.log(this.arr5);
  //     }
  //   }
  // }
};
</script>

<style>
</style>