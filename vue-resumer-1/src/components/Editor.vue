<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active:currentTab===i}" v-on:click="currentTab=i">
          <svg class="icon">
            <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
          </svg>
        </li>

      </ol>
    </nav>
    <ol class="panes">
      <li v-bind:class="{active:currentTab===0}">
        <ProfileEditor v-bind:items="resume.profile" v-bind:labels="{name:'姓名',city:'工作内容',birthday:'出生年月'}"
                       title="个人信息"></ProfileEditor>
      </li>
      <li v-bind:class="{active:currentTab===1}">

        <ArrayEditor v-bind:items="resume.workHistory" v-bind:labels="{company:'公司',content:'工作内容'}"
                     title="工作经历"></ArrayEditor>
      </li>
      <li v-bind:class="{active:currentTab===2}">
        <ArrayEditor v-bind:items="resume.studyHistory" v-bind:labels="{school:'学校',duration:'时间',degree:'学位'}"
                     title="学习经历"></ArrayEditor>
      </li>
      <li v-bind:class="{active:currentTab===3}">
        <ArrayEditor v-bind:items="resume.projects" v-bind:labels="{name:'项目名称',content:'内容'}" title="项目经历"></ArrayEditor>
      </li>
      <li v-bind:class="{active:currentTab===4}">
        <ArrayEditor v-bind:items="resume.awards" v-bind:labels="{name:'奖励详情'}" title="获奖情况"></ArrayEditor>
      </li>
      <li v-bind:class="{active:currentTab===5}">
        <ProfileEditor v-bind:items="resume.contacts" v-bind:labels="{qq:'QQ',wechat:'微信',email:'邮箱',phone:'手机'}"
                       title="联系方式"></ProfileEditor>
      </li>

    </ol>
  </div>

</template>
<script>
  import ProfileEditor from './ProfileEditor'
  import ArrayEditor from './ArrayEditor'


  export default {
    props:['resume'],
    data() {
      return {
        currentTab: 0,
        icons: ['shenfenzheng', 'work', 'book', 'heartsurgery', 'jiangbei', 'phone']
      }
    },
    components: {ProfileEditor, ArrayEditor},
    created() {

    },
    methods: {}
  }
</script>
<style lang="scss">
  #editor {
    min-height: 100px;
    display: flex;

    > nav {
      background: #000;
      width: 80px;

      > ol > li {
        padding: 16px 0;
        text-align: center;

        > .icon {
          width: 24px;
          height: 24px;
          fill: white;
        }

        &.active {
          background: white;
          overflow: auto;

          > .icon {
            fill: black;
          }
        }
      }
    }

    > .panes {
      flex: 1;
      .container {
        position: relative;
        .el-icon-cirle-close {
          position: absolute;
          right: 0;
          top: 0;
        }
      }

      > li {
        display: none;
        padidng: 32px;
        height: 100%;
        overflow: auto;

        &.active {
          display: block;
        }
      }
    }
  }

</style>
