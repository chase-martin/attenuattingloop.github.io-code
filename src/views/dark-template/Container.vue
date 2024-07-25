<template>
  <v-app id="dark-template">
    <v-fade-transition
      mode="out-in"
      type="animation"
    >
      <v-content>
        <v-container
          fluid
          fill-height
        >
          <v-layout
            align-center
            justify-center
          >
            <v-flex
              md10
              sm12
            >
              <v-layout
                align-center
                justify-center
              >
                <v-flex
                  xs6
                  sm8
                >
                  <sidebar-container class="" />
                  <content-container class="" />
                </v-flex>
              </v-layout>
              <v-layout
                align-center
                justify-center
              >
                <timeline-primary />
              </v-layout>
            </v-flex>
          </v-layout>
        </v-container>
      </v-content>
    </v-fade-transition>
  </v-app>
</template>

<script>
import SidebarContainer from '@/views/dark-template/sidebar/Container'
import ContentContainer from '@/views/dark-template/content/Container'
import TimelinePrimary from '@/views/dark-template/timeline/Primary'

export default {
  name      : 'DarkTemplateContainer',
  components: {
    TimelinePrimary,
    ContentContainer,
    SidebarContainer,
  },
}
</script>

<style lang="scss">
@import "@/scss/global.scss";
#dark-template {
  background: #66668d;
  background: -webkit-linear-gradient(to left, #66668d, #4389a2);
  background: linear-gradient(to left, #66668d, #4389a2);
  background-size: cover;
}
</style>
