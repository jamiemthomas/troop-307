<template>
  <div class="card">
      <g-image
        :src="form.cover_image"
        :alt="form.title"
        class="card-image"
      />
    <div class="card-content">
      <h1
        class="is-size-4 has-text-weight-bold"
      >
        {{ form.title }}
      </h1>
      <p
        v-html="form.content"
        class="content"
      />
    </div>
    <footer class="card-footer" v-if="form.buttons">
      <a
        class="card-footer-item"
        v-for="(button, index) in form.buttons"
        :key="index"
        :href="button.link"
        target="_blank"
      >
        {{ button.label }}
      </a>
    </footer>
  </div>
</template>

<style scoped>
  .card-image {
    margin: 0 auto; 
    display: block;
    object-fit: contain;
    max-height: 500px;
  }
</style>

<script>
export default {
  props: {
    form: {
      type: Object,
      default() {
        return {};
      },
    },
  },
};
</script>
