<script lang="ts" setup>

import { ElIcon } from 'element-plus'
import { Message, Star } from '@element-plus/icons-vue'
import { Document, Files, MagicStick, Picture, DataAnalysis, Film } from '@element-plus/icons-vue'
import Banner from "./Banner.vue"

// logo地址，没有则置为""即可
const logo = ''

// 标题
const title = 'Euclid’s Gift: Enhancing Spatial Perception and Reasoning in Vision-Language Models via Geometric Surrogate Tasks'

// 标题颜色
const title_color = '#000000'

// 标题补充，没有则置为''即可
const title_supp = ''

// 标题补充颜色
const title_supp_color = '#42B883'

// 按钮颜色
const btn_color = '#444444'

// 作者清单（包含作者姓名、头像、主页、地址序号）
const authors = [
  {
    name: "Shijie Lian",
    icon: "",
    homepage: "https://github.com/LiamLian0727",
    address_flag: "1,2",
    isEqual: true
  },
  {
    name: "Changti Wu",
    icon: "",
    homepage: "https://github.com/ChangtiWu",
    address_flag: "3,2",
    isEqual: true
  },
  {
    name: "Laurence Tianruo Yang",
    icon: "",
    homepage: "",
    address_flag: "4,1",
    isCorresponding: true
  },
  {
    name: "Bin Yu",
    icon: "",
    homepage: "https://github.com/yubinCloud",
    address_flag: "2"
  },
  {
    name: "Hang Yuan",
    icon: "",
    homepage: "https://github.com/Faustrazor",
    address_flag: "3"
  },
  {
    name: "Lei Zhang",
    icon: "",
    homepage: "",
    address_flag: "3"
  },
  {
    name: "Kai Chen",
    icon: "",
    homepage: "",
    address_flag: "5",
    isCorresponding: true
  },
]

// 地址清单（包含地址名称、头像、主页、地址序号）
const addresses = [
{
    address_flag: "1",
    name: "Huazhong University of Science and Technology",
    icon: "./HUST.jpg",
    homepage: "https://www.hust.edu.cn/"
  },
  {
    address_flag: "2",
    name: "Zhongguancun Academy",
    icon: "./ZGC.jpg",
    homepage: "http://bjzgca.edu.cn/"
  },
  {
    address_flag: "3",
    name: "East China Normal University",
    icon: "./ECNU.jpg",
    homepage: "https://www.ecnu.edu.cn/"
  },
  {
    address_flag: "4",
    name: "Zhengzhou University",
    icon: "./ZZU.png",
    homepage: "https://www.zzu.edu.cn/"
  },
  {
    address_flag: "5",
    name: "Zhongguancun Institute of Artificial Intelligence",
    icon: "./ZGCA.jpg",
    homepage: "https://zgci.ac.cn//"
  }
]

// 强调内容
const emphases = [
  "🎉 Accepted by CVPR 2026 Findings",
  // "🥰 欢迎关注“减论”微信公众号/B站/知乎/小红书",
  // "传递人工智能算法科普教育的减约理解",
  // "提升信息效率及认知维度"
]

// 提供引导资料链接
const buttons = [
  {
    disabled: false,
    name: "Paper",
    link: "https://arxiv.org/abs/2509.24473",
    component: Document,
  },
  {
    disabled: false,
    name: "Code",
    link: "https://github.com/LiamLian0727/Euclids_Gift",
    component: Files,
  },
  {
    disabled: false,
    name: "Dataset",
    link: "https://huggingface.co/datasets/LiamLian0727/Euclid30K",
    component: MagicStick,
  },
  // {
  //   disabled: true,
  //   name: "Poster",
  //   component: Picture,
  // },
  // {
  //   disabled: true,
  //   name: "Slide",
  //   component: DataAnalysis,
  // },
]

</script>

<template>
  <div>

    <!-- 最新消息提示
    <el-row justify="center">
      <el-col :span="24">
        <el-alert title="🔥 This paper has not been formally published yet." type="success" />
      </el-col>
    </el-row> -->

    <!-- Logo显示 -->
    <el-row v-if="logo" justify="center">
      <img :src="logo" alt="Logo" class="logo" />
    </el-row>

    <!-- 文章标题 -->
    <el-row justify="center">
      <el-col :span="20">
        <h1 class="paper-title">
          <span v-if="title" :style="{color:title_color}"> {{ title }}</span>
          <span v-if="title_supp" :style="{color:title_supp_color}"> {{ title_supp }}</span>
        </h1>
      </el-col>
    </el-row>

    <!-- 作者名单 -->
    <el-row justify="center">
      <template v-for="(author, idx) in authors">
        <a :href="author.homepage" target="_blank" rel="noopener noreferrer">
          <el-button class="title-button" type="primary" text>
            <el-avatar v-if="author.icon" :size="40" :src="author.icon" />
            <span class="author">
              {{ author.name }}
              <sup v-if="author.address_flag" class="name_sup">{{ author.address_flag }}</sup>
              <sup v-if="author.isEqual" class="name_sup">
                <el-icon :size="14"><Star /></el-icon>
              </sup>
              <sup v-if="author.isCorresponding" class="name_sup">
                <el-icon :size="14"><Message /></el-icon>
              </sup>
            </span>
          </el-button>
        </a>
        <!-- 在 Yang 后面插一个换行 -->
        <br v-if="author.name.includes('Laurence Tianruo Yang')" />
      </template>
    </el-row>


    <!-- 地址名单 -->
    <el-row justify="center">
      <a :href=address.homepage v-for="address in addresses" target="_blank" ref="noopener noreferrer">
        <el-button class="title-button" type="primary" text>
          <el-avatar v-if="address.icon" :size="40" :src="address.icon" />
          <span class="address">
            <sup v-if="address.address_flag" class="address_sup">{{ address.address_flag }}</sup>{{ address.name }}
          </span>
        </el-button>
      </a>
    </el-row>

    <!-- 共一和通讯提示内容 -->
    <el-row justify="center" class="con-cor">
      <el-icon :size="14" style="margin-right:4px;"><Star /></el-icon> These authors contributed equally, 
      <el-icon :size="14" style="margin:0 4px;"><Message /></el-icon> Corresponding author.
    </el-row>


    <!-- 强调内容 -->
    <el-row justify="center" class="emphasis" v-for="emphasis in emphases">
        {{ emphasis }}
    </el-row>

    <!-- 提供引导按钮 -->
    <el-row justify="center" style="margin-bottom: 20px;">
      <el-col :span="20">
        <el-row justify="center">
          <a :href=button.link v-for="button in buttons">
            <el-button class="guidance-button" size="default" :color="btn_color" :disabled="button.disabled" round>
              <el-icon :size="18">
                <component :is="button.component" />
              </el-icon>
              <span class="btn-text">{{ button.name }}</span>
            </el-button>
          </a>
        </el-row>
      </el-col>
    </el-row>

    <!-- Architecture -->
    <el-row justify="center">
    <img 
      src="/arch.png" 
      alt="Enhancing Spatial Perception and Reasoning Capabilities in Models Using the Geometric Problem-Solving Dataset (Euclid30K)." 
      style="width: 80%; max-width: 1000px; height: auto;"
    />
  </el-row>

  </div>
</template>

<style scoped>

/* 文章标题字体、字间距、居中排布、字号 */
.paper-title {
  font-family: "MyFont", Verdana, sans-serif;
  letter-spacing: 2px;
  font-size: 42px;
  margin: 32px;
  text-align: center;
}

/* 姓名和地址按钮 */
.title-button {
  margin: 10px 3px;
}

/* 姓名和地址按钮光标悬浮 */
.title-button:hover {
  margin: 10px 8px;
}

/* 引导材料按钮 */
.guidance-button {
  margin: 8px 5px;
  box-shadow: #d8d8d8 1px 1px 1px 1px;
}

/* 姓名属性 */
.author {
  font-size: 18px;
  margin-left: 3px;
}

/* 姓名上标属性 */
.name_sup {
  color: #606266; 
  margin-left: 3px;
}

/* 地址属性 */
.address {
  font-size: 18px;
}

/* 地址上标属性 */
.address_sup {
  color: #606266; 
  margin-right: 1px;
}

/* 头像属性 */
.el-avatar {
  margin-right: 6px;
  box-shadow: #b7b7b7 0px 0px 3px 1px;
}

/* 共一和通讯文字属性 */
.con-cor {
  font-family: Arial;
  font-size: 14px;
  margin: 18px 0px;
  text-align: center;
}

/* 强调信息属性 */
.emphasis {
  color: chocolate;
  font-weight: bold;
  margin: 8px;
  font-size: 22px;
  text-align: center;
}

/* 引导材料按钮文字属性 */
.btn-text {
  font-size: 18px;
  color: #ffffff;
}

.el-alert {
  margin: 10px 0 0;
}

.el-alert:first-child {
  margin: 0;
}

.logo {
  width: 150px; 
  height: 150px;
  border-radius: 50%;
  box-shadow: #ced3dc 0px 0px 3px 2px;
  margin-top: 40px;
}

/* 手机端链接样式处理 */
a:-webkit-any-link {
  text-decoration: none;
}

/* 取消鼠标焦点悬浮在链接上的颜色装饰 */
a:hover {
  color: inherit;
  border-bottom: none;
}

/* 链接装饰，取消下划线和链接颜色 */
a {
	text-decoration: None;
	color: inherit;
}

</style>
