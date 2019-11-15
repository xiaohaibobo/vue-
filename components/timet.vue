<template>
  <div>
    <div class="rest-title">
      <div class="restTcont">
        <p>选择项目时间</p>
        <el-row class="logout">
          <el-button class="logoutBtn" @click="logout">退出</el-button>
        </el-row>
      </div>
    </div>
    <div id="ptList">
      <el-checkbox-group v-model="arr" class="check-group" ref="fuxuan">
        <el-checkbox v-for="(d,i) in data" :key="i" :label="d.updated_at" class="ptcont" border></el-checkbox>
      </el-checkbox-group>
    </div>
    <div id="footer4">
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
       arr4: {}
    };
  },
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ path: "/login" });
    },

    after() {
      this.$router.push({ path: "/firstpt" });
    },
    next() {
      this.$router.push({ path: "/headico" });
      this.arr4 = this.arr[0];
      this.$store.dispatch("setDatao", this.arr4);
    }
  },
  computed: {
    data() {
      return this.$store.state.data;
    }
  }
};
</script>

<style>
</style>