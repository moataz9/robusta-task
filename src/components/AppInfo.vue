<template>
  <div class="app-info">
    <div class="left">
      <h2 class="town">{{ appTown }}</h2>
      <div class="date">{{ new Date().toDateString() }}</div>
      <img class="weather-icon" :src="iconSource" />
      <div class="weather-description">{{ weatherDescription }}</div>
    </div>
    <!--  -->
    <div class="right">
      <h2 class="degree">{{ degree }}°</h2>
      <div class="degree-details">
        <span class="day">{{ dayDegree }}°</span> / <span class="night">{{ nightDegree }}°</span>
      </div>
      <h3 class="day-status">{{ dayStatus }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    appTown: {
      type: String,
      required: true,
    },
    iconSource: {
      type: String,
      requierd: true,
    },
    weatherDescription: {
      type: String,
      requierd: true,
    },
    degree: {
      type: [String, Number],
      requierd: true,
    },
    dayDegree: {
      type: [String, Number],
      requierd: true,
    },
    nightDegree: {
      type: [String, Number],
      requierd: true,
    },
    dayStatus: {
      type: String,
      requierd: true,
    },
  },
}
</script>

<style lang="scss">
.app-info {
  display: flex;
  justify-content: space-between;
  margin-top: 2rem;
  color: #fff;
  .left {
    .town {
      font-size: 64px;
      margin: 0;
    }
    .date {
      font-size: 20px;
    }
    .weather-icon {
      margin-top: 15px;
      max-width: 250px;
      width: 200px;
    }
    .weather-description {
      font-size: 30px;
      margin-top: 1rem;
      font-weight: bold;
    }
  }
  .right {
    .degree {
      font-size: 144px;
      margin: 0;
    }
    .degree-details {
      font-size: 48px;
      .night {
        color: rgba($color: #fff, $alpha: 0.25);
      }
    }
    .day-status {
      font-size: 24px;
      font-weight: 600;
    }
  }
}
</style>
