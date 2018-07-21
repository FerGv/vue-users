<template lang="pug">
  div.card
    div.card-image
      figure.image.is-128x128
        img(:src="user.picture.large" :alt="fullName")

    div.card-content
      div.media
        div.media-left
          figure.image.is-48x48
            img(:src="user.picture.thumbnail" :alt="fullName")

        div.media-content
          p.title.is-4(v-text="fullName")
          p.subtitle.is-6(v-text="user.email")

      div.content
        p #[b Calle]: #[span(v-text="user.location.street")]
        p #[b Ciudad]: #[span(v-text="user.location.city")]
        p #[b Estado]: #[span(v-text="user.location.state")]
        p #[b Código Postal]: #[span(v-text="user.location.postcode")]
</template>

<script>
export default {
  props: ['user'],
  computed: {
    fullName() {
      return `${this.user.name.title} ${this.user.name.first} ${this.user.name.last}`
    }
  }
}
</script>

<style lang="sass" scoped>

</style>
