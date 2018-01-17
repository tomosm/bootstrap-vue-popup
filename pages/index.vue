<template>
  <div id="popup-container">
    <b-btn id="show-popup" variant="info" class="m-1">
      Show Popup
    </b-btn>

    <popup
      container="popup-container"
      target="show-popup"
      placement="bottom">
      Hi!
    </popup>
  </div>
</template>

<script>
  import Popup from '~/components/Popup'

  export default {
    components: {
      Popup
    }
  }
</script>
