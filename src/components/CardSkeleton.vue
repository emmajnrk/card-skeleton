<template>
  <v-card :class="cardIsPadded">
    <card-skeleton-header v-if="hasHeader"></card-skeleton-header>
    <v-container v-if="isHorizontal">
      <v-layout row align-center>
        <v-flex class="flex--grow">
          <card-skeleton-text :lines="lines"></card-skeleton-text>
        </v-flex>
        <v-flex>
          <card-skeleton-media
            :height="`${getMediaHeight}`"
            :width="`${getMediaWidth}`"
            v-if="hasMedia"
          ></card-skeleton-media>
        </v-flex>
      </v-layout>
    </v-container>
    <v-layout column v-else>
      <v-flex>
        <card-skeleton-media
          :height="`${getMediaHeight}`"
          :width="`${getMediaWidth}`"
          v-if="hasMedia"
        ></card-skeleton-media>
      </v-flex>
      <v-flex>
        <card-skeleton-text :lines="lines" v-if="hasText"></card-skeleton-text>
      </v-flex>
    </v-layout>
    <card-skeleton-actions v-if="hasActions"></card-skeleton-actions>
  </v-card>
</template>

<script>
import CardSkeletonHeader from "./CardSkeletonHeader/CardSkeletonHeader.vue";
import CardSkeletonMedia from "./CardSkeletonMedia/CardSkeletonMedia.vue";
import CardSkeletonText from "./CardSkeletonText/CardSkeletonText.vue";
import CardSkeletonActions from "./CardSkeletonActions/CardSkeletonActions.vue";

export default {
  props: {
    hasHeader: {
      default: true
    },
    hasMedia: {
      default: true
    },
    hasText: {
      default: true
    },
    hasActions: {
      default: false
    },
    isHorizontal: {
      default: false
    },
    lines: {
      default: 2
    },
    mediaHeight: {
      type: Number | String,
      default: 150
    },
    mediaWidth: {
      type: Number | String,
      default: "auto"
      // validator: (prop) =>{typeof e === 'string'}
    },
    cardIsPadded: {
      default: "pa-0"
    }
  },
  components: {
    CardSkeletonHeader,
    CardSkeletonMedia,
    CardSkeletonText,
    CardSkeletonActions
  },
  data: function() {
    return {};
  },
  methods: {},
  computed: {
    getMediaHeight() {
      console.log(this.mediaHeight);
      if (typeof this.mediaHeight == "number") {
        return `${this.mediaHeight}px`;
      } else {
        return this.mediaHeight;
      }
    },
    getMediaWidth() {
      console.log(this.mediaWidth);
      if (typeof this.mediaWidth == "number") {
        return `${this.mediaWidth}px`;
      } else {
        return this.mediaWidth;
      }
    }
  }
};
</script>

<style>
.flex--grow {
  flex-grow: 99 !important;
}
</style>