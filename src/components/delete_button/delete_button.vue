<template>
  <div v-if="canDelete">
    <a href="#" v-on:click.prevent="deleteStatus()">
      <i class='icon-cancel delete-status'></i>
    </a>
  </div>
</template>

<script src="./delete_button.js" ></script>

<style lang="scss">
@import '../../_variables.scss';

.icon-cancel,.delete-status {
  cursor: pointer;
  &:hover {
    color: var(--cRed, $fallback--cRed);
    color: $fallback--cRed;
  }
}
</style>
