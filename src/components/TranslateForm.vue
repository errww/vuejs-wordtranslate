<template>
  <div id="translateForm">
    <hr>
    <form v-on:submit="formSubmit" class="card card-body bg-light">
      <div class="form-group row">
        <div class="col-sm-6">
          <input type="text" v-model="textToTranslate" placeholder="Enter a word in English" class="form-control mr-sm-2">
        </div>
        <div class="col-sm-2"> 
          <select v-model="language" class="form-control">
        <option value="ru">Russian</option>
        <option value="jv">Javanesee</option>
      </select>
        </div>
        <div class="col-sm-2">
          <input type="submit" value="Translate" class="btn btn-primary">
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data(){
    return{
      textToTranslate:'',
      language:''
    }
  },
  created(){
    this.language = 'jv';
  },
  methods: {
    formSubmit(e){
      this.$emit('formSubmit', this.textToTranslate, this.language);
      e.preventDefault();
    }
  }
}
</script>

<style>

</style>
