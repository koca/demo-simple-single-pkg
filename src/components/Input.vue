<script>
import { defineComponent, attrsListenersMixin } from '@vue-bridge/runtime'

export default defineComponent({
  name: 'Input',
  mixins: [attrsListenersMixin()],
  props: {
    modelValue: {
      type: String,
      required: true,
    },
  },
  emits: ['update:modelValue'],
  computed: {
    model: {
      get() {
        return this.modelValue
      },
      set(v) {
        this.$emit('update:modelValue', v)
      },
    },
  },
})
</script>
<template>
  <div>
    <label for="input">
      <input
        v-model="model"
        type="text"
        v-bind="$_attrs"
      >
    </label>
  </div>
</template>
