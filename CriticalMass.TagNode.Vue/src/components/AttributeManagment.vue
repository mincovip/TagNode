<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>这是一个测试页面(属性提交)</h2>
       <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Vue Axios Post - ProductChain</div>
    
                    <div class="card-body">
                        <form @submit="formSubmit">
                        <strong>Name:</strong>
                        <input type="text" class="form-control" v-model="name">
                        <strong>Description:</strong>
                        <textarea class="form-control" v-model="description"></textarea>
    
                        <button class="btn btn-success">Submit</button>
                        </form>
                        <strong>Output:</strong>
                        <pre>
                        {{output}}
                        </pre>
                    </div>
                </div>
            </div>
        </div>
    </div>
  </div>


</template>

<script>
export default {
  mounted() {
    console.log('Component mounted.')
  },
  name: 'Test',
  data () {
    return {
      msg: '属性添加测试',
      name: '',
      description: '',
      output: '',
      jsonStr:"{attrId:0,attrName:\"类目\",canMultiSelect:0,canNull:0,canCustom:0,createBy:1,ctype:\"tree\",subValues:[{attrValId:0,val:\'服饰\',subValues:[{attrValId:0,val:\'青年款\',subValues:[]},{attrValId:0,val:\'儿童款\',subValues:[]},{attrValId:0,val:\'中老年款\',subValues:[]}]},{attrValId:0,val:\'食品\',subValues:[{attrValId:0,val:\'面包\',subValues:[]},{attrValId:0,val:\'坚果\',subValues:[]},{attrValId:0,val:\'方便面\',subValues:[]}]}]}"
    }
  },
  methods: {
            formSubmit(e) {
                e.preventDefault();
                let currentObj = this;
                this.axios({
                  method: 'post',
                  url: 'http://172.16.0.111/api/Attribute/AddOrModifyAttribute',
                  params: {
                    jsonStr: this.jsonStr
                  },
                  headers: {'Content-Type': 'x-www-form-urlencoded','Accept':'*'}
                })
                .then(function (response) {
                    currentObj.output = response.data;                   
                })
                .catch(function (error) {
                    currentObj.output = error;
                });
            }
        }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
