<template>
  <section class="my_dialog_container">
    <el-dialog
      :title='title'
      :visible.sync="dialogFormVisible"
      :modal='modal'
      :top='top'
      :close-on-click-modal='false'
    >
      <el-form label-width="80px">
        <slot>
          <el-form-item label='内容'>
            <el-input></el-input>
          </el-form-item>
        </slot>
        <el-form-item v-if='title==="弹窗1"' label="选择内容">
          <el-select
            placeholder="请选择活动区域"
            v-model="region"
            @click.native="selectClick"
          >
            <el-option
              label="shanghai"
              value="shanghai"
            ></el-option>
            <el-option
              label="beijing"
              value="beijing"
            ></el-option>
          </el-select>
        </el-form-item>
      </el-form>
      <div
        slot="footer"
        class="dialog-footer"
      >
        <el-button
          type="primary"
          @click="buttonClick"
        >{{buttonName}}</el-button>
      </div>
    </el-dialog>
  </section>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      default: "默认标题"
    },
    buttonName: {
      type:String,
      default: '更 多'
    },
    modal: {
      type:Boolean,
      default: true
    },
    top: {
      type:String,
      default:'15vh'
    },
    region: {
      type:String,
      default:''
    }
  },
  data() {
    return {
      dialogFormVisible: false
    };
  },
  methods: {
    selectClick() {
      this.$emit('selectFunc')
    },
    buttonClick() {
      this.$emit('childFunc')
    }
  }
};
</script>
