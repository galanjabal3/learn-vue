<template>
  <div id="app">
    <h1 style="text-align: center">{{ judul }}</h1>
      <div class="body">
        <Form 
        :getContent='addContent'
        :same='sameData'
        @addData="addData"
        @emptyForm='emptyFormAfterDelete'
      />
      <home
        :listOfData="listOfData"
        @gantiJudul="changeJudul"
      />
    </div>    
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import Form from "./components/Form.vue";

export default {
  name: "App",
  data() {
    return {
      judul: "Learn Vue",
      listOfData: ["Data 1", "Data 2", "Data 3"],
      onClick: 0,
      addContent: '',
      sameData: false,
      saveIndex: ''
    };
  },
  components: {
    Home,
    Form,
  },
  methods: {
    changeJudul(data) {
      // this.judul = data;
      this.onClick++
      if (this.onClick >= 1) {
        this.addContent = this.listOfData[data]
        this.saveIndex = data
      }
      if (this.onClick >= 2) {
        let confirm = window.confirm("Delete " + this.listOfData[data] + " ?")
        if (confirm) {
          this.sameData = true
          this.listOfData.splice(data, 1) 
          this.saveIndex = ''
        } 
        this.onClick = 0
      }
      setTimeout(() => {
        this.onClick = 0
      }, 700);
    },
    emptyFormAfterDelete() {
      this.sameData = false
    },
    addData(data) {
      if (this.saveIndex === '') {
        this.listOfData.push(data)
      } else {
        this.listOfData[this.saveIndex] = data
        this.listOfData.push(11111)
        this.listOfData.splice(this.listOfData.length -1,1)
        this.saveIndex = ''
      }
      // sessionStorage.setItem('Data', data)
    }
  },
};
</script>

<style>
* {
  font-family:cursive;
  max-width: 1440px;
  margin: auto;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  width: 80%;
  margin-top: 50px;
}
</style>

