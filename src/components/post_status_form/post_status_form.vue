<template>
  <div class="post-status-form">
    <form v-on:submit.prevent="postStatus(newStatus)">
      <div class="form-group" >
        <textarea v-model="newStatus.status" placeholder="Just landed in L.A." rows="3" class="form-control"></textarea>
      </div>
      <div class="attachments">
        <div class="attachment" v-for="file in newStatus.files">
          <img class="thumbnail media-upload" :src="file.image"></img>
        </div>
      </div>
      <div class='form-bottom'>
        <media-upload files="newStatus.files"></media-upload>
        <button type="submit" class="btn btn-default" >Submit</button>
      </div>
    </form>
  </div>
</template>

<script src="./post_status_form.js"></script>