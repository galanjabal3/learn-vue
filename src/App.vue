<template>
  <div id="app">
    <h1 style="text-align: center">{{ judul }}</h1>
      <div class="body">
        <Form 
        @addData="addData"
        :getContent='addContent'
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
      addContent: ''
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
      }
      if (this.onClick >= 2) {
        let confirm = window.confirm("Delete " + this.listOfData[data] + " ?")
        if (confirm) {
          this.listOfData.splice(data, 1) 
        } 
        this.onClick = 0
      }
      setTimeout(() => {
        this.onClick = 0
      }, 700);
    },
    addData(data) {
      this.listOfData.push(data)
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

