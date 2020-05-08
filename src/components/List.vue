<template>
  <div>
    <b-input-group prepend="Input" class="mt-5">
      <b-form-input v-model="inputTask" @keypress.enter="add" placeholder="Enter Task"></b-form-input>
      <b-input-group-append>
        <b-button variant="info" @click="add">Enter</b-button>
      </b-input-group-append>
    </b-input-group>
    <hr />
    <b-list-group>
      <b-list-group-item
        class="d-flex justify-content-between align-items-left list"
        v-bind:style="col(index)"
        v-for="(td, index) in this.tasks"
        :key="index"
      >
        <input type="checkbox" id="checkbox" class="my-auto" v-model="td.done" />

        <div class="textTodo">{{ td.todo}}</div>

        <b-button-group>
          <button type="button" class="close mr-3" aria-label="Close" @click="showModal(index)">
            <span>
              <b-icon-pen class="small"></b-icon-pen>
            </span>
          </button>

          <button type="button" class="close" aria-label="Close" @click="fetch(index)">
            <b-icon-x class="small"></b-icon-x>
          </button>
        </b-button-group>
      </b-list-group-item>
    </b-list-group>

    <b-modal ref="my-modal" hide-footer title="Edit Task">
      <div class="d-block text-center">
        <b-input-group prepend="Task Input" class="mt-3">
          <b-form-input v-model="tempTask" @keypress.enter="saveModal" @keypress.esc="cancelModal"></b-form-input>
        </b-input-group>
      </div>
      <b-form-row>
        <b-col>
          <b-button class="mt-5" variant="outline-success" block @click="saveModal">Save Task</b-button>
        </b-col>
        <b-col>
          <b-button class="mt-5" variant="outline-danger" block @click="cancelModal">Cancel</b-button>
        </b-col>
      </b-form-row>
    </b-modal>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputTask: null,
      tempTask: null,
      curval: null,
      tasks: [
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
      this.curval = val;
      this.tempTask = this.tasks[val].todo;
    },
    saveModal() {
      this.tasks[this.curval].todo = this.tempTask;
      this.$refs["my-modal"].hide();
      this.curval = null;
    },
    cancelModal() {
      this.$refs["my-modal"].hide();
    },
    col(index) {
      console.log(index);
      if (this.tasks[index].done)
        return { backgroundColor: `rgb(170, 212, 181)` };
      return { backgroundColor: `rgb(236, 213, 178)` ,
      
      };
    }
  }
};
</script>
<style scoped>
.textTodo {
  word-break: break-all;
  margin: 2% 5%;
  /* background-color: rgb(236, 213, 178); */
  font-size: 125%;
}
</style>