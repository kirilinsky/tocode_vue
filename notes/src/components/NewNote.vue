<template>
  <div class="new-note">
    <label for="title">title</label>
    <input id="title" v-model="note.title" type="text" />
    <label for="desc">description</label>
    <textarea
      id="desc"
      name="desc"
      v-model="note.description"
      cols="30"
      rows="10"
    ></textarea>
    <button class="btn btnPrimary" @click="addNote">add new</button>
  </div>
</template>

<script>
export default {
  props: {
    note: {
      type: Object,
      required: true,
    },
  },
  methods: {
    addNote() {
      this.$emit("addNote", this.note);
    },
  },
};
</script>

<style lang="scss" scoped>
.new-note {
  text-align: center;
}
</style>
