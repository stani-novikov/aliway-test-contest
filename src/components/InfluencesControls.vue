<template>
  <section class="controls">
    <div class="controls__column">
      <span class="controls__title controls__title--no-pointer">
        Инфлюенсер
      </span>
    </div>
    <div class="controls__column">
      <span class="controls__title"
            :class="{
            'controls__title--active' : activeSortingParam === 'followers',
            'controls__title--increase' : !isSortByIncrease
            }"
            @click="$emit('sortTable', {
              sortParam: 'followers'
            })"
      >
        Подписчиков
      </span>
      <span class="controls__icon"></span>
    </div>
    <div class="controls__column">
      <span class="controls__title"
            :class="{
             'controls__title--active' : activeSortingParam === 'er',
             'controls__title--increase' : !isSortByIncrease
             }"
            @click="$emit('sortTable', {
              sortParam: 'er'
            })"
      >
        Уровень вовлеченности
      </span>
      <span class="controls__icon"></span>
    </div>
  </section>
</template>

<script>
export default {
  name: "InfluencesControls",
  props: {
    activeSortingParam: {
      type: [Object, String]
    },
    isSortByIncrease: {
      type: Boolean
    }
  },
  data() {
    return {
      subscribersParam: 'increase',
    }
  },
  created() {
    console.log(this.isSortByIncrease)
  }
}
</script>

<style>
.controls {
  display: flex;
  margin-bottom: 10px;
}

.controls__column {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 33%;
  padding-bottom: 10px;
  border-bottom: 2px solid #e5e5e5;
}

.controls__title {
  cursor: pointer;
}

.controls__icon {
  position: relative;
  top: -3px;
  display: inline-block;
  margin-left: 10px;
  width: 10px;
  height: 10px;
  border-top: 2px solid #000;
  border-left: 2px solid #000;
  transform: rotateZ(225deg);
}

.controls__title--active {
  color: cornflowerblue;
}

.controls__title--active + .controls__icon {
  border-color: cornflowerblue;
}

.controls__title--increase + .controls__icon {
  top: 3px;
  transform: rotateZ(45deg);
}

.controls__title--no-pointer {
  cursor: default;
}
</style>