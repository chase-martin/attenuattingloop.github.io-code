<template>
  <v-card
    color="lighten-4"
    light
  >
    <v-card-text>
      <content-section
        :title="abouts.title"
      >
        {{ abouts.description }}
      </content-section>
      <content-section
        v-if="!educations"
        :title="titles.education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}, {{ education.to }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="skills"
        id="to-timeline"
        :title="titles.skills"
      >
        <template slot="actions" />
        <v-layout wrap>
          <template
            v-for="(skill, i) in skills"
          >
            <v-flex
              v-if="skill.divider"
              :key="i"
              md12
              xs12
              mb-4
            />
            <v-flex
              v-else
              :key="'~'+i"
              md12
              xs12
            >
              <div
                class="mr-2 ml-2"
              >
                <div class="align-center">
                  <v-icon medium>
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
import { educations, skills, abouts, titles } from '@/content/resume.json'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({
    abouts,
    educations,
    skills,
    titles,
  }),
}
</script>

<style scoped>
.v-icon{
  vertical-align: middle;
  margin-right: 10px;
}
.progress {
  margin-top: 0.1rem;
}

</style>
