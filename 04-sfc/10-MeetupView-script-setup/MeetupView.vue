<script setup>
import { UiAlert, UiContainer } from '@shgk/vue-course-ui'
import MeetupAgenda from './MeetupAgenda.vue'
import MeetupDescription from './MeetupDescription.vue'
import MeetupCover from './MeetupCover.vue'
import MeetupInfo from './MeetupInfo.vue'

const props = defineProps({
  meetup: {
    type: Array,
    required: true,
  },
})
</script>

<template>
  <div>
    <UiContainer>
      <MeetupCover :title="props.meetup.title" :image="props.meetup.image" />

      <div class="meetup">
        <div class="meetup__content">
          <h2>Описание</h2>
          <MeetupDescription :description="props.meetup.description" />

          <h2>Программа</h2>

          <UiAlert v-if="props.meetup.agenda.length === 0" type="info"> Программа пока пуста... </UiAlert>

          <MeetupAgenda v-else :agenda="props.meetup.agenda" />
        </div>

        <div class="meetup__aside">
          <MeetupInfo :organizer="props.meetup.organizer" :place="props.meetup.place" :date="props.meetup.date" />
          <div class="meetup__aside-buttons"></div>
        </div>
      </div>
    </UiContainer>
  </div>
</template>

<style scoped>
.meetup {
  display: flex;
  flex-direction: column;
  margin: 48px 0 0;
}

.meetup__content {
}

.meetup__aside {
  margin: 40px 0;
}

.meetup__aside-buttons {
  padding: 0 0 0 34px;
  margin-top: 16px;
}

.meetup__aside-button {
  margin: 0 10px 10px 0;
}

@media all and (min-width: 992px) {
  .meetup {
    flex-direction: row;
  }

  .meetup__content {
    flex: 1 0 calc(100% - 350px);
  }

  .meetup__aside {
    flex: 1 0 350px;
    padding: 50px 0 0 44px;
    margin: 0;
  }
}
</style>
