<template>
  <Tile
    :width="width"
    :height="height"
    :title="title"
    :color="color">
    <div class="detail">
      <slot name="before"/>
    </div>
    <div>
      <span
        class="value"
        v-html="value.toFixed(decimalPlaces)"
      /><span
        v-if="unit"
        class="unit"
        v-html="unit"
      />
    </div>
    <div class="detail">
      <slot name="after"/>
    </div>
  </Tile>
</template>

<script>
import Tile from './Tile.vue';

export default {
  components: {
    Tile,
  },

  extends: Tile,

  props: {
    value: {
      type: Number,
      default: NaN,
    },
    decimalPlaces: {
      type: Number,
      default: 0,
    },
    unit: {
      type: String,
      default: null,
    },
  },
};
</script>

<style scoped lang="scss">
  @import "~@/styles/vars.scss";
  .value {
    font-size: 2em;
    font-weight: bold;
  }
  .detail {
    max-width: 100%;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    color: $secondary-font;
  }
  .unit {
    font-size: 0.8em;
    font-weight: bold;
  }
</style>
