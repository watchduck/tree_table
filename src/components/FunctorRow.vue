<template>
  <tr @mouseover="handleMouseover" @mouseleave="handleMouseleave"
    :class="{bg2: highlight}">

    <td :class="{light: newNameDifferent}">{{funstr}}</td>

    <td>{{arity}}</td>

    <td class="customName">
      <input type="text" v-model="customName" :class="{red: error}">
    </td>

  </tr>
</template>

<script>
  export default {
    computed: {
      funstr() {
        return this.functor.name
      },
      arity() {
        return this.functor.ary
      },
      customName: {
        get() {
          return this.functor.tcname
        },
        set(val) {
          this.$store.dispatch('actCustomName', {
            id: this.id,
            val: val
          })
        }
      },
      highlight() {
        return this.id == this.focus.functor
      },
      functors() {
        return this.$store.state.output.functors
      },
      focus() {
        return this.$store.state.focus
      },
      error() {
        return this.$store.state.errorsCustomName.includes(this.id)
      },
      newNameDifferent() {
        return this.functor.name != this.functor.cname
      }
    },
    methods: {
      handleMouseover() {
        this.$store.commit('mutFocus', {
          knot: null,
          functor: this.id
        })
      },
      handleMouseleave() {
        this.$store.commit('mutUnfocus')
      }
    },
    props: ['functor', 'id']
  }
</script>
