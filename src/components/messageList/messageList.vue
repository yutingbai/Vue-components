<template>
  <div class="calculate frame-main-body">
    <div class="searchBox">
      <a-tabs @change="callback" type="card">
        <a-tab-pane tab="按照发送人搜" key="1">
          <a-form class="formBox" :form="form" @submit="handleSubmit" :layout="formLayout">
            <a-form-item label="输入用户名">
              <a-input v-decorator="['data']" style="width: 200px" />
            </a-form-item>
            <a-form-item>
              <a-button type="primary" html-type="submit">Search</a-button>
            </a-form-item>
          </a-form>
        </a-tab-pane>
        <a-tab-pane tab="按照时间搜" key="2">
          <a-form class="formBox" :form="form" @submit="handleSubmit" :layout="formLayout">
            <a-form-item label="输入日期区间">
              <a-range-picker v-decorator="['RangerPicker']" />
            </a-form-item>
            <a-form-item>
              <a-button type="primary" html-type="submit">Search</a-button>
            </a-form-item>
          </a-form>
        </a-tab-pane>
        <a-tab-pane tab="按照消息类型" key="3">
          <a-form class="formBox" :form="form" @submit="handleSubmit" :layout="formLayout">
            <a-form-item label="选择消息类型">
              <a-select v-decorator="['select']" style="width: 200px">
                <a-select-option value="SysMessage">系统消息</a-select-option>
                <a-select-option value="PriMessage">私信</a-select-option>
              </a-select>
            </a-form-item>
            <a-form-item>
              <a-button type="primary" html-type="submit">Search</a-button>
            </a-form-item>
          </a-form>
        </a-tab-pane>
      </a-tabs>
    </div>
    <a-divider orientation="left">消息列表</a-divider>
    <div class="DemoBox" v-for="(item,index) in messageList" :key="item.title + index">
      <a-card :title="item.title" size="small" :hoverable="true">
        <span slot="extra">{{item.type}}</span>
        <a-comment>
          <div slot="actions" v-for="item in  actions(item.status,item.type)" :key="item">
            <span class="tagBox" v-if="item">
              <a-tooltip >
                {{item}}
              </a-tooltip>
            </span>
          </div>
          <a slot="author">{{item.author}}</a>
          <a-avatar :src="item.avatar" :alt="item.author" slot="avatar" />
          <p slot="content">{{item.content}}</p>
          <a-tooltip slot="datetime" :title="moment(item.datetime).format('YYYY-MM-DD HH:mm:ss')">
            <span>{{moment(item.datetime,"YYYY-MM-DD").fromNow()}}</span>
          </a-tooltip>
        </a-comment>
      </a-card>
    </div>
  </div>
</template>
<script>
import moment from "moment";
moment.locale("zh-cn");
export default {
  name: "addFunc",
  props: ["messageList"],
  data() {
    return {
      likes: 0,
      dislikes: 0,
      action: null,
      moment,
      formLayout: "inline",
      form: this.$form.createForm(this, { name: "coordinated" }),
      a: this.num1 ? this.num1 : 0,
      b: this.num2 ? this.num2 : 0,
      sum: 0
    };
  },
  mounted() {
 
  },
  methods: {
    callback(key) {
      var _this = this
      this.$emit("callback",_this,key)
    },
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        const data =
          values.RangerPicker != undefined
            ? [
                values.RangerPicker[0].format("YYYY-MM-DD"),
                values.RangerPicker[1].format("YYYY-MM-DD")
              ]
            : undefined || values.select || values.data || "allDemo";
        if (!err) {
          console.log(data)
          this.$emit("search",data)
        }
      });
    },
    actions(status, type) {
      return [
        status === "true" ? " 已读 " : " 未读 ",
        type == "系统消息" ? undefined : " 回复 "
      ];
    }
  }
};
</script>
<style>
.calculate {
  width: 100%;
  line-height: 26px;
}
.formBox {
  margin-top: 30px;
  margin-bottom: 10px;
}
.DemoBox {
  width: 98%;
  margin: 0 auto;
  margin-bottom: 5px;
  margin-top: 5px;
}
.tagBox{
  margin-top: 20px;
  margin-right: 10px;
}
</style>