<template>
  <div class="influencer">
    <div class="influencer__column influencer__avatar">
      <div class="influencer__img-container">
        <a :href="influencer.profileUrl">
          <img :src="influencer.avatarUrl" :alt="influencer.name">
        </a>
      </div>
      <div class="influencer__name">
        @{{ influencer.name }}
      </div>
    </div>
    <div class="influencer__column influencer__subscribers">{{ influencer.followers }}</div>
    <div class="influencer__column influencer__involvement">{{ influencer.er }} %</div>
  </div>
</template>

<script>
export default {
  name: 'influencer',
  props: {
    influencer: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>

.influencer {
  box-sizing: border-box;
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
  padding: 5px;
  border-bottom: 1px solid #e5e5e5;
}

.influencer:hover {
  background-color: lightblue;
}

.influencer__img-container {
  max-width: 100px;
}

.influencer__img-container img {
  width: 100%;
  height: auto;
  display: block;
  border-radius: 50%;
}

.influencer__name {
  margin-top: 10px;
}

.influencer__column {
  display: flex;
  width: 33%;
  justify-content: center;
  align-items: center;
}

.influencer__avatar {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}
</style>