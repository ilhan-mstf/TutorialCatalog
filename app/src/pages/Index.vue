<template>
  <q-page>
    <div class="row justify-center q-mt-lg">
      <div class="col-6">
        <q-input
          outlined
          v-model="searchText"
          placeholder="Search"
        />
        <q-card
          v-for="item in items"
          :key="item.id"
          class="q-mt-lg"
        >
          <q-card-section>
            <div class="text-h6">{{ item.title }}</div>
            <div class="text-subtitle2">{{ item.subTitle }}</div>
            <q-badge
              v-for="(tag, index) in item.tags"
              :key="index"
              color="blue q-mr-sm"
            >
              {{ tag }}
            </q-badge>
          </q-card-section>
          <q-card-section class="q-pt-none">
            <q-video
              :ratio="16/9"
              :src="item.videoSrc"
            />
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
const videoTutorialData = [
  {
    id: 'vtPkZShrvXQ',
    title: 'Spring Boot Tutorial for Beginners (Java Framework)',
    subTitle: 'Course by Amigoscode on freeCodeCamp.org',
    tags: ['Spring', 'Java', 'API', 'Amigoscode', 'freeCodeCamp.org'],
    videoSrc: 'https://www.youtube.com/embed/vtPkZShrvXQ'
  },
  {
    id: 'Ke7Tr4RgRTs',
    title: 'Spring Boot - Getting started with Spring Boot (EASY)',
    subTitle: 'Course by Amigoscode',
    tags: ['Spring', 'Java', 'API', 'Amigoscode'],
    videoSrc: 'https://www.youtube.com/embed/Ke7Tr4RgRTs'
  }
]

export default {
  name: 'PageIndex',
  data () {
    return {
      searchText: '',
      items: videoTutorialData
    }
  },
  watch: {
    searchText: function () {
      if (this.searchText !== '') {
        const searchTextLower = this.searchText.toLowerCase()
        this.items = videoTutorialData.filter(i => i.title.toLowerCase().indexOf(searchTextLower) !== -1)
      }
    }
  }
}
</script>
