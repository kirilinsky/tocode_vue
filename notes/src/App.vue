<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section class="section">
        <div class="container">
          <h1>{{ title }}</h1>

          <!-- messages -->
          <Message v-if="message" :message="message" />

          <!-- new note -->
          <NewNote :note="note" @addNote="addNote" />
          <div class="icons">
            <img
              @click="grid = true"
              :class="{ active: grid }"
              src="./assets/grid.svg"
              alt="grid"
            />
            <img
              @click="grid = false"
              :class="{ active: !grid }"
              src="./assets/column.svg"
              alt="column"
            />
          </div>
          <!-- note  list -->
          <Notes :grid="grid" :notes="notes" @remove="removeNote" />
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import Message from "./components/Message";
import NewNote from "./components/NewNote";
import Notes from "./components/Notes";
export default {
  components: {
    Message,
    NewNote,
    Notes,
  },
  data() {
    return {
      title: "Notes App",
      message: null,
      grid: true,
      note: {
        title: "",
        description: "",
      },
      notes: [
        {
          title: "first note",
          description: "description for first note",
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: "second note",
          description: "description for second note",
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: "third note",
          description: "description for third note",
          date: new Date(Date.now()).toLocaleString(),
        },
      ],
    };
  },
  methods: {
    addNote() {
      let { title, description } = this.note;
      if (title === "") {
        this.message = "title cant be blank";
        return;
      }
      if (description === "") {
        this.message = "description cant be blank";
        return;
      }
      this.notes.push({
        ...this.note,
        date: new Date(Date.now()).toLocaleString(),
      });
      this.note.title = "";
      this.note.description = "";
      this.message = null;
    },
    removeNote(index) {
      this.notes.splice(index, 1);
    },
  },
};
</script>

<style lang="scss">
.icons {
  display: flex;
  align-items: center;
  justify-content: space-between;
  img {
    cursor: pointer;
    &.active {
      background: #c05858;
      border-radius: 3px;
      padding: 3px;
    }
  }
}
</style>
