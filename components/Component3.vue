<template>
  <div>
    Component 3!

    <v-select
      :value="value"
      :items="items"
      label="Seletor de componentes"
      multiple
      @input="$emit('input', $event)"
    />
  </div>
</template>

<script>
export default {
  props: {
    value: { type: Array, required: true },
  },

  data () {
    return {
      items: [
        'component4',
        'component5',
        'component6',
      ],
    }
  }, 
}
</script>
