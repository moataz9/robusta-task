<template>
  <div class="app-header">
    <h1 class="app-name">{{ appName }}</h1>
    <div class="c-and-f">
      <button :class="`c-deg ${activeBtn === 'c' ? 'active' : ''}`" @click="$emit('deg', 'c')">℃</button>
      <button :class="`f-deg ${activeBtn === 'f' ? 'active' : ''}`" @click="$emit('deg', 'f')">℉</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    appName: {
      type: String,
      required: true,
    },
    activeBtn: {
      type: String,
      required: true
    }
  },
  emits: ['deg']
}
</script>

<style lang="scss">
.app-header {
  display: flex;
  justify-content: space-between;
  .app-name {
    color: #fff;
    text-transform: uppercase;
  }
  .c-and-f {
    display: flex;
    align-items: center;
    .c-deg,
    .f-deg {
      font-size: 1.3rem;
      background-color: transparent;
      border: none;
      width: 3.8rem;
      padding: 8px 0;
      color: #fff;
      cursor: pointer;
      &.active {
        background-color: rgba(255, 255, 255, 0.25);
        border-left: 1px solid #fff;
      }
    }
    .c-deg {
      margin-right: 10px;
    }
  }
}
</style>
