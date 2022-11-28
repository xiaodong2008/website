<template>
  <router-view v-slot="{ Component }">
    <transition appear mode="out-in">
      <component :is="Component"/>
    </transition>
  </router-view>
</template>

<style lang="less">
.v-enter-from, .v-leave-to {
  opacity: 0;
}

.v-enter-active, .v-leave-active {
  transition: all .35s;
}
</style>