<template>
  <status v-if="notification.type === 'mention'" :compact="true" :statusoid="notification.status"></status>
  <div class="non-mention" v-else>
    <a class='avatar-container' :href="notification.action.user.statusnet_profile_url" @click.stop.prevent.capture="toggleUserExpanded">
      <StillImage class='avatar-compact' :src="notification.action.user.profile_image_url_original"/>
    </a>
    <div class='notification-right'>
      <div class="usercard notification-usercard" v-if="userExpanded">
        <user-card-content :user="notification.action.user" :switcher="false"></user-card-content>
      </div>
      <span class="notification-details">
        <div class="name-and-action">
          <span class="username" :title="'@'+notification.action.user.screen_name">{{ notification.action.user.name }}</span>
          <span v-if="notification.type === 'favorite'">
            <i class="fa icon-star lit"></i>
            <small>{{$t('notifications.favorited_you')}}</small>
          </span>
          <span v-if="notification.type === 'repeat'">
            <i class="fa icon-retweet lit"></i>
            <small>{{$t('notifications.repeated_you')}}</small>
          </span>
          <span v-if="notification.type === 'follow'">
            <i class="fa icon-user-plus lit"></i>
            <small>{{$t('notifications.followed_you')}}</small>
          </span>
        </div>
        <small class="timeago"><router-link :to="{ name: 'conversation', params: { id: notification.status.id } }"><timeago :since="notification.action.created_at" :auto-update="240"></timeago></router-link></small>
      </span>
      <div class="follow-text" v-if="notification.type === 'follow'">
        <router-link :to="{ name: 'user-profile', params: { id: notification.action.user.id } }">@{{notification.action.user.screen_name}}</router-link>
      </div>
      <status v-else class="faint" :compact="true" :statusoid="notification.status" :noHeading="true"></status>
    </div>
  </div>
</template>

<script src="./notification.js"></script>
