<template>
  <div class="notifications">
    <div class="panel panel-default">
      <div class="panel-heading">
        <span class="unseen-count" v-if="unseenCount">{{unseenCount}}</span>
        {{$t('notifications.notifications')}}
        <button v-if="unseenCount" @click.prevent="markAsSeen" class="read-button">{{$t('notifications.read')}}</button>
      </div>
      <div class="panel-body">
        <div v-for="notification in visibleNotifications" :key="notification.action.id" class="notification" :class='{"unseen": !notification.seen}'>
          <notification :notification="notification"></notification>
        </div>
      </div>
    </div>
  </div>
</template>

<script src="./notifications.js"></script>
<style lang="scss" src="./notifications.scss"></style>
