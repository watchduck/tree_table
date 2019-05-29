<template>
  <td @mouseover="handleMouseover"
      @mouseleave="handleMouseleave"
      :colspan="cell.span"
      :class="{bold: highlight.bold, bg2: highlight.bg2}">
    {{display}}
  </td>
</template>

<script>
  export default {
    computed: {
      functors() {
        return this.$store.state.output.functors
      },
      knot_to_functor() {
        return this.$store.state.output.knots
      },
      knot() {
        return this.cell.entry
      },
      functor() {
        return this.knot_to_functor[this.knot]
      },
      focus() {
        return this.$store.state.focus
      },
      display() {
        let functor_index = this.knot_to_functor[this.knot];
        let name_or_cname = this.$store.state.showCustomName ? 'cname' : 'name';
        return this.functors[functor_index][name_or_cname]
      },
      highlight() {
        let bold = this.knot == this.focus.knot;
        return {
          bold: bold,
          bg2: !bold && this.functor == this.focus.functor
        }
      }
    },
    methods: {
      handleMouseover() {
        this.$store.commit('mutFocus', {knot: this.knot, functor: this.functor})
      },
      handleMouseleave() {
        this.$store.commit('mutUnfocus')
      }
    },
    props: ['cell']
  }
</script>

