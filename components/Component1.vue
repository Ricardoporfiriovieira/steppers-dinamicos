<template>
  <div>
    Component 1!

    <v-text-field
      :value="value"
      label="Campo de teste"
      @input="$emit('input', $event)"
    />
  </div>
</template>

<script>
export default {
  props: {
    value: { type: String, required: true },
  },
}
</script>
