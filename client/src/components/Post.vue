<template lang="pug">
  div
    .post.card
      h4.card-header {{ title }}
      .card-body
        div(v-if="tags.length && tags[0].name")
          router-link(v-for="tag in tags" :key="tag.name" :to="{ name: 'ShowPostsByTag', params: { name: tag.name }}" class="badge badge-primary mx-1") {{ tag.name }}
          
        div(v-html="body")
        router-link(:to="{ name: 'ShowPost', params: { friendlyUrl: this.friendlyUrl }}") Czytaj dalej
        blockquote.blockquote.mb-0
          footer.blockquote-footer
            | Autor: {{ author }} | utworzono: {{ createdAt|prettyDate }}

</template>
<script>
export default {
  name: 'post',
  props: ['title', 'body', 'createdAt', 'author', 'friendlyUrl', 'tags'],
};
</script>
