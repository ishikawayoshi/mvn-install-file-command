<template>
  <div id="app">
    <div class="container">
      <b-row>
        <b-col md="3">
          <h2>Please add</h2>
          <b-form-input class="mt-2" id="input-small" size="sm" type="text" @input="updateDep" v-model="dependency.groupId" placeholder="Enter groupId"></b-form-input>
          <b-form-input class="mt-2" id="input-small" size="sm" type="text" @input="updateDep" v-model="dependency.artifactId" placeholder="Enter artifactId"></b-form-input>
          <b-form-input class="mt-2" id="input-small" size="sm" type="text" @input="updateDep" v-model="dependency.version" placeholder="Enter version"></b-form-input>
          <b-form-input class="mt-2" id="input-small" size="sm" type="text" @input="updateDep" v-model="dependency.path" placeholder="Enter path to jar"></b-form-input>
        </b-col>
        <b-col md="9">
          <h2>Dependency result</h2>
          <!-- <div v-html="dep"></div> -->
          <pre>{{dep}}</pre>
        </b-col>
      </b-row>
      <b-row>
        <b-col md="12">
          <h2>Command to install jar to local m2</h2>
          <pre>{{this.install}}</pre>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      dep: null,
      dependency:{
        groupId:"",
        artifactId:"",
        version:"",
        path:""
      },
      install:""

    }
  },methods:{
    updateDep(){
      this.dep = 
      `       <dependency>
          <groupId>${this.dependency.groupId}</groupId>
          <artifactId>${this.dependency.artifactId}</artifactId>
          <version>${this.dependency.version}</version>
        </dependency>`;
      this.install = `mvn install:install-file -Dfile=${this.dependency.path}  -DgroupId=${this.dependency.groupId} -DartifactId=${this.dependency.artifactId} -Dversion=${this.dependency.version} -Dpackaging=jar`
    }
  }
}
</script>

<style lang="scss">

h1, h2 {
  font-weight: normal;
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
