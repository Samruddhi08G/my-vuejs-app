
<template>
  <div class="hello">
     <h1>{{msg}}</h1>
    <h1>Filter LearnVue Articles</h1>
          
      <div class="search-wrapper">
        <input type="text" name="title" v-model="search" placeholder="Search title.."/>
      </div>
      <div>
        <button type="button" class="btn-primary"  @click='resetForm'>Reset</button>
       </div>
       <div style="margin-top: 20px;">
       <div v-for="r of resultQuery" :key="r.id">{{r.title}}</div>
       </div>

  </div>
    
</template>

<script>

export default {
  name: 'HelloWorld',
  
     data() {
    return {
      search: null,
      resources: [
        { id: 1, title: "javascript for dummies" },
        { id: 2, title: "vue for dummies" },
        { id: 3, title: "dos for dummies" },
        { id: 4, title: "windows for dummies" },
        { id: 5, title: "html for dummies" }
      ]
    };
  },
   methods:{
    resetForm() { 
        this.search = ''; 
        
   }
	},
  computed: {
    resultQuery() {
      if (this.search) {
        return this.resources.filter(item => {
          return this.search
            .toLowerCase()
            .split(" ")
            .every(v => item.title.toLowerCase().includes(v));
        });
      } else {
        return this.resources;
      }
    }
  }
};

 
 
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
input[type="text"] {
    height: 25px;
    width: 20%;
}

button.btn-primary{
   margin-top: 20px;
    height: 32px;
    width: 100px;
    color: #fff;
    background-color: #337ab7;
    border-color: #2e6da4;
    border: none;
}
</style>
