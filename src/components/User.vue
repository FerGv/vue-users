<template lang="pug">
  .column.is-half-tablet.is-one-third-desktop.is-one-quarter-fullhd
    .card
      .card-image
        figure.image.is-4by3
          img(:src="user.picture.large" :alt="fullName")

      .card-content
        .media
          .media-left
            figure.image.is-48x48
              img(:src="user.picture.thumbnail" :alt="fullName")

          .media-content
            p.title.is-4(v-text="fullName")
            p.subtitle.is-6(v-text="user.email")

        .content
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
