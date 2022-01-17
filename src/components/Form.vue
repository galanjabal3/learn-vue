<template>
  <div class="todo-form">
    <input type="text" v-model="addContent" class="input"/>
    <button @click="addDataContent">Add</button>
  </div>
</template>

<script>
export default {
  name: "form",
  data() {
    return {
      addContent: "",
    };
  },
  props: {
    getContent: {
      type: String,
      required: true
    }
  },
  watch: {
    getContent(v){
      this.addContent = v 
    }
  },
  methods: {
    addDataContent() {
      if(this.addContent === "") {
        alert('Form harus di isi')
        return 
      }
      this.$emit('addData', this.addContent)
      this.addContent = ''
    },
  },
};
</script>

<style scoped>
.input {
  width: 100%;
  height: 35px;
}
.todo-form {
  text-align: center;
  display: flex;
  padding: 20px 0px;
}

.todo-form button {
  width: 100px;
  height: 41px;
  color: white;
  background-color: blue;
}
</style>