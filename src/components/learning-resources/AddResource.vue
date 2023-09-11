<template>
  <teleport to="body">
    <error-modal @closeBtn="closeModal" v-if="inputValid"> </error-modal>
  </teleport>
  <base-card>
    <form @submit.prevent="submitFormData">
      <div class="form-control">
        <label for="title">Title</label>
        <input
          v-model="inputTitle"
          id="title"
          name="title"
          type="text"
          ref="titleInput"
        />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          v-model="inputDesc"
          id="description"
          name="description"
          rows="3"
          ref="descInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input
          v-model="inputLink"
          id="link"
          name="link"
          type="url"
          ref="linkInput"
        />
      </div>
      <div class="form-btn">
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseCard from '../ui/BaseCard.vue';
import ErrorModal from '../layouts/ErrorModal.vue';

export default {
  components: { BaseCard, ErrorModal },
  inject: ['resource', 'addResource'],
  //영상강좌에서는 ref 사용함.
  //refHTML 요소 $refs로 접근가능함.
  //주석으로 표시함.
  data() {
    return {
      inputTitle: '',
      inputDesc: '',
      inputLink: '',
      inputValid: false,
    };
  },

  methods: {
    submitFormData() {
      // this.resource.push({
      // id: Date.now(),
      // title: this.inputTitle,
      // title: this.$refs.titleInput.value
      // description: this.inputDesc,
      // description: this.$refs.descInput.value
      // link: this.inputLink,
      // link: this.$refs.linkInput.value
      //});
      if (
        this.inputTitle.trim() === '' ||
        this.inputDesc.trim() === '' ||
        this.inputLink.trim() === ''
      ) {
        this.inputValid = true;
        return;
      }
      this.addResource(this.inputTitle, this.inputDesc, this.inputLink);
      this.inputTitle = '';
      this.inputDesc = '';
      this.inputLink = '';
    },

    closeModal(valid) {
      this.inputValid = valid;
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  padding: 1rem;
  width: 100%;
  margin: 0;
}
.form-control {
  display: flex;
  flex-direction: column;
  margin: 1rem;
  width: 100%;
}
label {
  font-weight: bold;
  margin-bottom: 0.5rem;
}
input {
  padding: 0.5rem;
  width: 80%;
}
textarea {
  padding: 0.5rem;
  width: 80%;
}
.form-btn {
  align-self: flex-start;
}
</style>
