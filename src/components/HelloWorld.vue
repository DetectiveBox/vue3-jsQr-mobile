<template>
  <div class="container">
    <div class="input-container">
      <a-input-search
        ref="qrInput"
        v-model="data.qrCode"
        autofocus
        placeholder="请扫描二维码"
        search-button
        class="w-p-90"
        @change="searchInfo"
        @press-enter="searchInfo"
        @search="searchInfo"
      >
        <template #prefix>
          <icon-scan @click="handleScan" />
        </template>
      </a-input-search>
    </div>
    <GetQrcode
      v-if="data.isQrCodeShown"
      @success="gotQrCode"
      @closeScan="closeScan"
    />
    <a-alert v-if="data.isQrAlert" closable>{{ data.qrCOdeData }}</a-alert>
  </div>
</template>

<script lang="ts" setup>
import { ref, reactive, onMounted } from "vue";
import { FormInstance } from "@arco-design/web-vue/es/form";
import GetQrcode from "./GetQrcode.vue";

const qrInput: any = ref<FormInstance>();

// 全局控制的数据
const data = reactive({
  qrCode: "",
  isQrCodeShown: false,
  isQrAlert: false,
  qrCOdeData: "",
});

// 输入框的search事件
const searchInfo = (val: any) => {
  console.log("查询");
  console.log(data.qrCode);
  if (qrInput.value) {
    qrInput.value.focus();
  }
};

// 点击扫描图标---打开扫码功能
const handleScan = () => {
  const isMobile = checkDevice();
  if (isMobile === true) {
    data.isQrCodeShown = true;
  }
};

// 检查当前登录设备类型
const checkDevice = () => {
  // 获取浏览器navigator对象的userAgent属性（浏览器用于HTTP请求的用户代理头的值）
  const info = navigator.userAgent;
  // 通过正则表达式的test方法判断是否包含“Mobile”字符串
  const isMobile = /mobile/i.test(info);
  // 如果包含“Mobile”（是手机设备）则返回true
  return isMobile;
};
// 扫码成功
const gotQrCode = (params: any) => {
  // 这里params就是二维码的内容，这里可以根据自己项目的需求处理内容
  if (params) {
    data.isQrAlert = true;
    data.qrCOdeData = params;  // 我这里拿到二维码的内容是弹出框弹出，为了测试
    data.isQrCodeShown = false;
  }
};

const closeScan = () => {
  // 开发的 时候为了方便，加了这个关闭按钮，正常项目可以去掉
  data.isQrCodeShown = false;
};
</script>

<script lang="ts">
export default {
  name: "Scan",
  data() {
    return {};
  },
};
</script>

<style lang="less" scoped>
.top-tip-txt,
.no-data {
  color: rgb(var(--gray-6));
}
.input-container {
  padding: 8px 0 16px;
}

@media (min-width: 992px) {
  .detail-info {
    display: flex;
    .device-img {
      flex: 0 0 100px;
    }
    .txt-info {
      flex: 1;
    }
  }
}
@media (max-width: 992px) {
  .detail-info {
    // display: flex;
    .device-img {
      margin-bottom: 16px;
    }
    .txt-info {
      // flex: 1;
    }
  }
}

.detail-info {
  // display: flex;
  .device-img {
    // flex: 0 0 100px;
    height: 100px;
    background-color: #eee;
  }
  .txt-info {
    // flex: 1;
    padding: 0 16px;
    .uuid-name {
      color: var(--base);
    }
    .desc {
    }
  }
}

.w-p-90 {
  width: 90%;
  margin-left: 5%;
}
</style>

<style lang="less" scoped>
// responsive
.mobile {
  .container {
    display: block;
  }
}
</style>
