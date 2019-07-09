<template>
  <div class="field">
          <label class="label">名前</label>
          <div class="control">
            <input class="input" type="text" name="name" required>
            <p class="help is-danger">名前を入力してください</p>
          </div>
        </div>
</template>

<script>
export default {
  name: 'FormInput',
  data: ()=>{

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
