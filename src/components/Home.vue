<template>
  <div>
    <h2>Data List</h2>
    <ul>
      <li
        style="cursor: pointer"
        v-for="(data, index) in listOfData"
        :key="index"
        @click="changeJudul(index)"
      >
        {{ data }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "home",
  props: {
    listOfData: {
      type: Array,
    },
    listOfDataObject: {
      type: Array,
    },
  },
  methods: {
    changeJudul(data) {
        this.$emit("gantiJudul", data);
    },
  },
};
</script>

<style scoped>
ul  li {
  border: 1px solid turquoise;
  padding: 10px;
  margin: 10px;
  cursor: pointer;
}

ul  li:hover {
  background: rgb(211, 42, 42);
  color: white;
}
</style>
