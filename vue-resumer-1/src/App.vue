<template>
  <div id="app" v-bind:class="{previewMode:previewMode}">
    <Topbar class="topbar" v-on:preview="preview"></Topbar>
    <main>
      <Editor v-bind:resume="resume" class="editor"></Editor>
      <Preview v-bind:resume="resume" class="preview"></Preview>

    </main>
    <el-button id="exitPreview" v-on:click="exitPreview"> 退出预览</el-button>
  </div>
</template>

<script>
  import Topbar from './components/Topvar'
  import Editor from './components/Editor'
  import Preview from './components/Preview'

  export default {
    data() {

      return {
        previewMode: false,
        resume: {
          profile: {
            name: '',
            city: '',
            birthday: ''
          },
          workHistory: [
            {company: '', content: ''}
          ],
          studyHistory: [{school: '', duration: '', degree: ''}],
          projects: [{name: '', content: ''}],
          awards: [{name: ""}],
          contacts: {
            qq: '',
            wechat: '',
            email: '',
            phone: ''
          }
        }
      }
    },
    methods: {
      preview() {
        this.previewMode = true
      },
      exitPreview(){
        this.previewMode = false
      }
    },
    components: {
      Preview,
      Editor,
      Topbar
    }
  }
</script>

<style lang="scss">
  html, body, #app {
    height: 100%;
    overflow: auto;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    height: 100vh;
    display: flex;
    flex-direction: column;
  }

  .topbar {
    position: relative;
    z-index: 1;
    box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
  }

  .icon {
    width: 1em;
    height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }

  main {

    display: flex;
    flex: 1;
    background: #DDD;

    > .editor {
      width: 40em;
      margin: 16px 8px 16px 16px;
      background: white;
      box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
      border-radius: 4px;
      overflow: hidden;
    }

    > .preview {
      flex: 1;
      margin: 16px 16px 16px 8px;
      background: white;
      box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
      border-radius: 4px;
      overflow: auto;

    }
  }

  .previewMode > #topbar {
    display: none;
  }

  .previewMode #editor {
    display: none;
  }

  .previewMode #preview {
    max-width: 800px;
    margin: 32px auto;
  }

  #exitPreview {
    display: none;
  }

  .previewMode #exitPreview {
    display: inline-block;
    position: fixed;
    right: 16px;
    bottom: 16px;
  }
</style>
