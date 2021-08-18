<template>
  <div>
    <influencer
        v-for="(influencer, index) in influencers"
        :key="index"
        :influencer="influencer"
    />
  </div>
</template>

<script>
import Influencer from "./InfluencerItem";
export default {
  name: 'InfluencesTable',
  components: {Influencer},
  props: {
    influencers: {
      type: Array,
      required: true,
    }
  }
}
</script>