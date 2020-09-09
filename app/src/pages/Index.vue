<template>
  <q-page>
    <div class="row justify-center q-mt-lg">
      <div class="col-3">
        <div class="q-ml-lg q-mr-sm">
          <h1 class="text-h5">Video Tutorial Catalog</h1>
          <h2 class="text-body1">
            Hand-picked catalog of tutorial videos that are shorter than 2 hours.
          </h2>
          <p>It is hard know every tool, framework, language, etc. However, you can learn the basics of them quickly under 2 hours.</p>
          <p>Your time is valuable.Therefore, only focus on what matters most.</p>
          <p>The aim is to provide best quality resources to learn <strong>important concepts of a topic</strong> without being lost in the detail and too many resources.</p>
          <q-btn
            color="black"
            type="a"
            href="https://github.com/ilhan-mstf/TutorialCatalog"
            target="_blank"
            label="Github Project"
            size="sm"
            icon="launch"
          />
        </div>
      </div>
      <div class="col-6 q-mb-lg">
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
            <div class="text-caption">by {{ item.author }} on {{ item.publisher }}</div>
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
      <div class="col-3"></div>
    </div>
  </q-page>
</template>

<script>
import videoTutorialData from 'src/data/videos'

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
