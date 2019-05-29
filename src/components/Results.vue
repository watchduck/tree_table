<template>
  <div>
    <a id="reset" @click="reset">back to input</a>

    <table id="main">
      <tr v-for="(row, rowindex) in table">
        <th class="rowindex">{{rowindex}}</th>
        <knot-cell v-if="cell.entry!='gap'"
               v-for="cell in row"
               :cell="cell"></knot-cell>
        <td v-else class="gap" :colspan="cell.span"></td>
      </tr>
    </table>

    <p id="formula">
      <formula-span v-for="obj in reco_list" :obj="obj"></formula-span>
    </p>

    <table id="functors">
      <tr>
        <th>name</th>
        <th>arity</th>
        <th>custom name</th>
      </tr>
      <functor-row v-for="(functor, id) in functors"
            :functor="functor"
            :id="id"></functor-row>
    </table>

    <input type="checkbox" v-model="showCustomName">
    <label>show custom names</label>
  </div>
</template>

<script>
  import Vue from 'vue';

  import FunctorRow from './FunctorRow.vue';
  import KnotCell from './KnotCell.vue';
  import FormulaSpan from './FormulaSpan.vue';

  export default {
    data() { return {
      reco_list: []  // elements of the recomposed formula, i.e. knots mapped to functors, brackets and commas
    }},
    computed: {
      functors() {
        return this.$store.state.output.functors
      },
      table() {
        return this.$store.state.output.table
      },
      tree() {
        return this.$store.state.output.tree
      },
      showCustomName: {
        get() {
          return this.$store.state.showCustomName
        },
        set(val) {
          this.$store.commit('mutShowCustomName', val)
        }
      },
    },
    methods: {
      reset() {
        this.$store.commit('mutReset')
      },
      recompose(d) {
        if (!Array.isArray(d)) {  // `d` is no array, thus an object ("dictionary")
          this.reco_list.push({'what': 'knot', 'which': d.knot});
          if (d.ary > 0) {
            this.reco_list.push({'what': 'bracket', 'which': 'open', 'knot': d.knot});
            this.recompose(d.arg);
            this.reco_list.push({'what': 'bracket', 'which': 'close', 'knot': d.knot});
          }
        } else {  // `d` is an array ("list")
          for (let item of d) {
            this.recompose(item);
            this.reco_list.push({'what': 'comma', 'knot': item.parent});
          }
          this.reco_list.splice(-1, 1);  // remove comma before closing bracket
        }
      }
    },
    mounted() {
      this.recompose(this.tree);
      for (let [id, functor] of this.functors.entries()) {
        // duplicate name as custom name (and temporary custom name) that can be edited
        this.$store.commit('mutCustomName', {id: id, val: functor.name})
      }
    },
    components: {FunctorRow, KnotCell, FormulaSpan}
  }
</script>
