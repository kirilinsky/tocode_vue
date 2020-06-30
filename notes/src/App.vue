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
          <!-- note  list -->
          <Notes :notes="notes" @remove="removeNote" />
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
    removeNote(index){
      this.notes.splice(index, 1)
    }
  },
};
</script>

<style></style>
