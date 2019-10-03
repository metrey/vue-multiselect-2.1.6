<template lang="pug">
div
  label.typo__label Single select / dropdown
  multiselect(
    v-model="value",
    deselect-label="Can't remove this value",
    track-by="name",
    label="name",
    placeholder="Select one",
    :options="options",
    :searchable="false",
    :allow-empty="false"
    :showDetail="true"
    @viewDetail="viewIt"
  )
    template(slot="singleLabel", slot-scope="{ option }")
      strong {{ option.name }}
      |  is written in
      strong   {{ option.language }}
  pre.language-json
    code.
      {{ value  }}

</template>

<script>
import Multiselect from 'vue-multiselect'

export default {
  components: {
    Multiselect
  },
  data () {
    return {
      value: null,
      options: [
        { name: 'Vue.js', language: 'JavaScript' },
        { name: 'Rails', language: 'Ruby' },
        { name: 'Sinatra', language: 'Ruby' },
        { name: 'Laravel', language: 'PHP', $isDisabled: true },
        { name: 'Phoenix', language: 'Elixir' }
      ]
    }
  },
  methods: {
    viewIt(event) {
      alert(JSON.stringify(event))
    }
  }
}
</script>

<style lang="css">
</style>
