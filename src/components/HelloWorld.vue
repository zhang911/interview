<template>
  <section class="hool_worid_container">
    <el-input v-model="main"></el-input>
    <el-button class="btn" size='mini' type="primary" @click='showSelect'>主要按钮</el-button>
    <MyDialog
      title="弹窗1"
      ref="MyDialog1"
      @childFunc="MyDialogFunc1"
      @selectFunc="MyDialogSelectFunc1"
      top='0vh'
      :region='region'
    ></MyDialog>
    <MyDialog
      title="弹窗2"
      ref="MyDialog2"
      @childFunc="MyDialogFunc2"
      buttonName="确定"
      top='0vh'
    >
      <ul>
        <li v-for="item in selectMain" @click='selectMainClick(item)' :key='item'>{{item}}</li>
      </ul>
    </MyDialog>
    <MyDialog
      title="弹窗3"
      ref="MyDialog3"
      @childFunc="MyDialogFunc3"
      buttonName="确定"
      :modal='false'
      top='50vh'
    ></MyDialog>
  </section>
</template>

<script>
import MyDialog from "./MyDialog";
export default {
  name: "HelloWorld",
  components: { MyDialog },
  data() {
    return {
      main: "",
      region: "",
      dialogTableVisible: false,
      dialogFormVisible: false,
      formLabelWidth: "120px",
      selectMain:['shanghai','beijing'],
      region:''
    };
  },
  methods: {
    showSelect() {
      this.$refs.MyDialog1.dialogFormVisible = true;
    },
    MyDialogFunc1() {
      this.$refs.MyDialog3.dialogFormVisible = true;
    },
    MyDialogFunc2() {
      this.$refs.MyDialog2.dialogFormVisible = false;
    },
    MyDialogFunc3() {
      this.$refs.MyDialog1.dialogFormVisible = false;
      this.$refs.MyDialog3.dialogFormVisible = false;
      this.main='选择完成'
    },
    MyDialogSelectFunc1() {
      this.$refs.MyDialog2.dialogFormVisible = true;
    },
    selectMainClick (item) {
      this.region = item
      console.log(item)
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn {
  margin: 0 auto;
}
</style>
