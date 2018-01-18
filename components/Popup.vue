<template>
  <b-popover
    class="popup"
    :container="container"
    :target="target"
    :show.sync="popupShow"
    :placement="placement">
    <slot></slot>
  </b-popover>
</template>

<script>
  export default {
    name: 'popup',
    data () {
      return {
        popupShow: false
      }
    },
    props: {
      container: {
        type: String,
        required: true
      },
      target: {
        type: String,
        required: true
      },
      placement: {
        type: String,
        default: 'auto'
      }
    },
    mounted: function () {
      let node = this.$el
      // Traverse to the parents to search the container node
      // because b-popover generates DOM which has the arrow class right beneath the container DOM
      while (!!node && node.id !== this.container) {
        node = node.parentNode
      }

      // If the container DOM is a sibling or child
      if (!node) {
        node = this.$el.parentNode.querySelector(`#${this.container}`)
      }

      if (node && node.classList) {
        node.classList.add('hide-arrow')
      }
    }
  }
</script>

<style lang="scss">
  .hide-arrow > .popover {
    .arrow {
      display: none;
    }
  }
</style>
