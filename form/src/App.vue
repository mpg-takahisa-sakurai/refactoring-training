<template>
  <div id="app">
    <div class="container">
      <form novalidate id="js-form" method="post" @submit.prevent="onSubmit">
        <div class="field">
          <label class="label">名前</label>
          <div class="control">
            <input v-model='name' class="input" type="text" name="name" required>
            <p v-show="nameError" class="help is-danger">名前を入力してください</p>
          </div>
        </div>

        <div class="field">
          <label class="label">年齢</label>
          <div class="control">
            <input v-model='age' class="input" type="number" min="0" max="130" name="age" required>
            <p v-show="ageError" class="help is-danger">年齢を入力してください</p>
          </div>
        </div>


        <div class="field">
          <label class="label">性別</label>
          <div class="control">
            <label class="radio">
              <input v-model='gender' type="radio" name="gender" value="男性" checked>
              男性
            </label>
            <label class="radio">
              <input v-model='gender' type="radio" name="gender" value="女性">
              女性
            </label>
          </div>
        </div>

        <div class="field">
          <label class="label">職業</label>
          <div class="control">
            <div class="select">
              <select v-model='job' name="job" id="js-job">
                <option>会社員</option>
                <option>自営業</option>
                <option>公務員</option>
                <option>学生</option>
                <option>その他</option>
              </select>
            </div>
          </div>
        </div>

        <div v-show="job_other" class="field field-option" id="js-job-name">
          <label class="label">職業名</label>
          <div class="control">
            <input v-model='jobName' class="input" type="text" name="job-name">
            <p v-show="jobNameError" class="help is-danger">職業名を入力してください</p>
          </div>
        </div>

        <div class="field">
          <label class="label">お問い合わせ内容</label>
          <div class="control">
            <textarea v-model='body' class="textarea" name="body" required></textarea>
            <p v-show="bodyError" class="help is-danger">お問い合わせ内容を入力してください</p>
          </div>
        </div>

        <div class="field">
          <div class="control">
            <label class="checkbox">
              規約に同意する <input v-model='agreement' type="checkbox" name="agreement" required>
              <p v-show="agreementError" class="help is-danger">規約に同意してください</p>
            </label>
          </div>
        </div>


        <div class="field">
          <div class="control">
            <button type="submit" class="button is-link">送信</button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  components: {
    // HelloWorld
  },
  data() {
    return {
      name: '',
      nameError: false,
      age: 0,
      ageError: false,
      gender: 0,
      job: '',
      jobName: '',
      jobNameError: false,
      body: '',
      bodyError: false,
      agreement: false
    }
  },
  computed: {
    job_other(){
      return this.job==='その他'
    }
  },
  methods: {
    validateAll(){
      this.nameError = !this.name
      this.ageError = !this.age
      this.jobNameError = !this.jobName
      this.bodyError = !this.body
    },
    validate(){
      this.validateAll()
      !this.nameError &&
      !this.ageError &&
      (!this.job_other || !this.jobNameError) &&
      !this.bodyError &&
      this.agreement
    },
    onSubmit(){
      if(this.validate()){

      }else{
        alert('入力エラーがあります')
      }
    }
  },
  watch: {
    name() {
      this.nameError = !this.name
    },
    age() {
      this.ageError = !this.age
    },
    jobName() {
      this.jobNameError = !this.jobName
    },
    body() {
      this.bodyError = !this.body
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
