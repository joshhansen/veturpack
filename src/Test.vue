<template>
  <div>
    {{ bar }}
  </div>
</template>

<script lang="ts">
import * as _ from 'lodash'
import { defineComponent } from 'vue';

export default defineComponent({
  props: ['foo', 'bar'],

  data() {
    return {
      count: 0,
    };
  },

  mounted() {
    // This does not give an error because `this.count` is seen as having type `any`
    const result = this.count.split('') // => Property 'split' does not exist on type 'number'

    // This does give an error, indicating that typechecking is working at least somewhat
    const n: number = 'abc';
  }
});
</script>