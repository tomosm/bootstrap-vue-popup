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
    }
  }
</script>

<style lang="scss">
  .popup + .popover {
    .arrow {
      display: none;
    }
  }
</style>
