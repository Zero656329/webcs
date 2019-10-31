<template>
  <div id="preview">
    <h1>{{resume.profile.name || '请填写姓名'}}</h1>
    <p>{{resume.profile.city ||'请填写城市'}}|{{resume.profile.birthday  ||'请填写出生年月'}}</p>
    <hr>
    <section v-if='filter(resume.workHistory).length>0'>
      <h2>工作经历</h2>
      <ul>
        <li v-for="work in filter(resume.workHistory)">
          {{work.company}}
          {{work.content}}
        </li>
      </ul>
    </section>
    <section v-if='filter(resume.studyHistory).length>0'>
      <h2>学习经历</h2>
      <ul>
        <li v-for="work in filter(resume.studyHistory)">
          {{work.company}}
          {{work.content}}
        </li>
      </ul>
    </section>
    <section v-if='filter(resume.projects).length>0'>
    <h2>项目</h2>
    <ul>
      <li v-for="project in filter(resume.projects)">
        {{project.name}}
        {{project.content}}
      </li>
    </ul>
  </section>
    <section v-if='filter(resume.awards).length>0'>
      <h2>获奖情况</h2>
      <ul>
        <li v-for="award in filter(resume.awards)">
          {{award.name}}
          {{award.content}}
        </li>
      </ul>
    </section>
    <hr>

    <p>{{resume.contacts.qq ||'请填写QQ'}}|{{resume.contacts.wechat  ||'请填写微信'}}|{{resume.contacts.email  ||'请填写电子邮箱'}}{{resume.contacts.phone  ||'请填写手机号码'}}</p>


  </div>

</template>
<script>
  export default {
    props: ['resume'],
    methods: {
      filter(array) {
        return array.filter(item => !this.isEmpty(item))
      },
      isEmpty(Object) {
        let empty = true
        for (let key in Object) {
          if (Object[key]) {
            empty = false
            break
          }
        }
      }
    }
  }
</script>


<style>
  #preview {
    border: 1px solid red;
    min-height: 100px;
  }

</style>
