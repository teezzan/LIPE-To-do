<template>
  <div>
    <input type="text" value placeholder="enter text" v-model="inputTask"  @keypress.enter="add"/>
    <button @click="add">Add</button>
    <hr />

    <b-list-group>
      <b-list-group-item
        class="d-flex justify-content-between align-items-center"
        v-for="(td, index) in this.tasks"
        :key="index"
      >
        {{ td.todo}}
        <button type="button" class="close" aria-label="Close" @click="fetch(index)">
          <span aria-hidden="true">&times;</span>
        </button>
      </b-list-group-item>
    </b-list-group>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputTask: null,
      tasks: [
        { todo: "Hello Lorem", done: false },
        { todo: "Ipsium Lorem", done: false },
        { todo: "Saola code", done: true }
      ]
    };
  },
  props: {
    // todo: Array
  },
  methods: {
    fetch(index) {
      console.log(index);
      this.tasks.splice(index, 1);
    },
    add() {
      if(this.inputTask =="" ||this.inputTask == null || this.inputTask == "  ") return
      this.tasks.push({todo: this.inputTask, done: false});
      this.inputTask = "";
    }
  }
};
</script>