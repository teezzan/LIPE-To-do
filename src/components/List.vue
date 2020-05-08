<template>
  <div>
    <b-input-group prepend="Task" class="mt-3">
      <b-form-input v-model="inputTask" @keypress.enter="add"></b-form-input>
      <b-input-group-append>
        <b-button variant="info" @click="add">Enter</b-button>
      </b-input-group-append>
    </b-input-group>
    <hr />

    <b-list-group>
      <b-list-group-item
        class="d-flex justify-content-between align-items-left"
        v-for="(td, index) in this.tasks"
        :key="index"
      >
        <input type="checkbox" id="checkbox" v-model="td.done" />

        <div class="lis">{{ td.todo}}</div>

        <b-button-group>
          <button type="button" class="close" aria-label="Close" @click="showModal(index)">
            <span aria-hidden="true">&times;</span>
          </button>

          <button type="button" class="close" aria-label="Close" @click="fetch(index)">
            <span aria-hidden="true">&times;</span>
          </button>
        </b-button-group>
      </b-list-group-item>
    </b-list-group>

    <b-modal ref="my-modal" hide-footer title="Edit Task">
      <div class="d-block text-center">
        <b-input-group prepend="Task" class="mt-3">
          <b-form-input v-model="inputTask" @keypress.enter="add"></b-form-input>
          <b-input-group-append>
            <b-button variant="info" @click="add">Enter</b-button>
          </b-input-group-append>
        </b-input-group>
      </div>

      <b-button class="mt-3" variant="outline-danger" block @click="hideModal">Close Me</b-button>
      <b-button class="mt-2" variant="outline-warning" block @click="toggleModal">Toggle Me</b-button>
    </b-modal>
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
      if (
        this.inputTask == "" ||
        this.inputTask == null ||
        this.inputTask == "  "
      )
        return;
      this.tasks.push({ todo: this.inputTask, done: false });
      this.inputTask = "";
    },
    showModal(val) {
      this.$refs["my-modal"].show();
      console.log(val);
    },
    hideModal() {
      this.$refs["my-modal"].hide();
    },
    toggleModal() {
      // We pass the ID of the button that we want to return focus to
      // when the modal has hidden
      this.$refs["my-modal"].toggle("#toggle-btn");
    }
  }
};
</script>
<style scoped>
.lis {
  word-break: break-all;
  margin: 2% 5%;
}
</style>