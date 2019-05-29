<template>
  <span @mouseover="handleMouseover" @mouseleave="handleMouseleave"
      :class=" {bold: highlight.bold, bg1: highlight.bg1, bg2: highlight.bg2}">{{display}}</span>
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
      what() {
        return this.obj.what
      },
      which() {
        if (this.what=='comma') {
          return null
        } else {
          return this.obj.which
        }
      },
      knot() {
        if (this.what=='knot') {
          return this.which
        } else {
          return this.obj.knot
        }
      },
      functor() {
        return this.knot_to_functor[this.knot]
      },
      display() {
        if (this.what=='knot') {
          let name_or_cname = this.$store.state.showCustomName ? 'cname' : 'name';
          return this.functors[this.functor][name_or_cname]
        } else if (this.what=='bracket') {
          return this.which=='open' ? '(' : ')'
        } else {
          return ', '
        }
      },
      focus() {
        return this.$store.state.focus
      },
      highlight() {
        let isText = this.what == 'knot';
        let bold = this.knot == this.focus.knot;
        return {
          bold: bold,
          bg1: isText && bold,
          bg2: !bold && isText && this.functor == this.focus.functor
        }
      }
    },
    methods: {
      handleMouseover() {
        this.$store.commit('mutFocus', {
          knot: this.knot,
          functor: this.functor
        })
      },
      handleMouseleave() {
        this.$store.commit('mutUnfocus')
      }
    },
    props: ['obj']
  }
</script>
