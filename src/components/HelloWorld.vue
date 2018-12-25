<template>
  <div>
    <input type="text" @keyup.enter="add" v-model="value" v-if="showAddButton">
    <input type="text" @keyup.enter="update" v-model="value" v-else>
    <button @click="add" v-if="showAddButton" >Add</button>
    <button @click="update" v-else> Update </button>
    <ul>
      <li v-for="(text,index) in list" :key="index">
        {{text}} 
        <button @click="remove(index)"> delete</button>
        <button @click="edit(index)"> Edit </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      value: '',
      list: [],
      indexEdited: null,
    }
  },
  computed: {
    showAddButton() {
      return this.indexEdited === null
    }
  },
  methods: {
    add() {
      this.list.push(this.value)
      this.value = ''
    },
    remove(index) {
      this.list.splice(index, 1)
    },
    edit(index) {
      this.value = this.list[index]
      this.indexEdited = index
    },
    update() {
      this.list[this.indexEdited] = this.value
      this.value = ''
      this.indexEdited = null
    }
  }
}

</script>
