<template>
  <div id="timeline">
    <h2>{{ titles.timeline }}</h2>
    <v-timeline dense>
      <v-timeline-item
        v-for="(item, i) in orderedItems"
        :key="i"
        :icon="item.icon || ''"
        :class="{transparent: item.transparent}"
        large
      >
        <template
          v-if="item.iconImage"
          v-slot:icon
        >
          <v-avatar>
            <img
              :src="publicPath(item.iconImage)"
            >
          </v-avatar>
        </template>
        <template v-slot:opposite />
        <v-layout>
          <v-flex xs12>
            <v-card class="elevation-1">
              <v-card-title class="pb-0">
                <div style="margin-bottom: -10px">
                  <h3>{{ item.title }}</h3>
                  <h4
                    v-if="item.company"
                    style="margin: 5px 0 10px 0"
                  >
                    {{ item.company }}
                  </h4>
                  <p>{{ item.dates }}</p>
                </div>
              </v-card-title>
              <v-card-text>
                <v-layout wrap>
                  <v-flex
                    :md7="!!item.image"
                    :md12="!item.image"
                    xs12
                  >
                    <div class="mr-1">
                      <!-- eslint-disable vue/no-v-html -->
                      <div
                        v-html="item.responsibilities"
                      />
                      <!-- eslint-enable vue/no-v-html -->
                    </div>
                  </v-flex>
                  <v-flex
                    v-if="item.image"
                    md5
                    xs12
                  >
                    <div
                      class="mt-2"
                    >
                      <v-carousel
                        v-if="Array.isArray(item.image)"
                        :show-arrows="false"
                        :height="325"
                      >
                        <v-carousel-item
                          v-for="(citem,ci) in item.image"
                          :key="ci"
                          :src="publicPath(citem)"
                        />
                      </v-carousel>
                      <v-img
                        v-else
                        :max-height="item.imageHeight ? item.imageHeight : ''"
                        :src="publicPath(item.image)"
                      />
                    </div>
                  </v-flex>
                </v-layout>
              </v-card-text>
            </v-card>
          </v-flex>
        </v-layout>
      </v-timeline-item>
    </v-timeline>
  </div>
</template>

<script>
import { timelines, titles } from '@/content/resume.json'
export default {
  name: 'Timeline',
  data: () => ({
    detailed: true,
    items   : timelines,
    titles,
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      if (this.detailed)
        return items
      return items.filter((item) => {
        return !item.detailed
      })
    },
  },
}
</script>

<style lang="scss" scoped>
#timeline{
  padding: 32px 0px 0px 16px;
  &>h2{font-weight: 300;}
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
.v-avatar{
  background-color: white;
  img{
    object-fit: contain;
    background-color:white;
    margin: 0 auto;
  }
}
</style>
