<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
      </q-toolbar>
      <div class="header-content">
        <div class="text-h3">Tarefas</div>
        <div class="text-subtitle">{{ todaysDate }}</div>
      </div>
      <q-img
        src="src/assets/imagens/02.png"
        class="header-image absolute-top"
      />
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="250"
      :breakpoint="600"
    >
      <q-scroll-area style="height: calc(100% - 185px); margin-top: 185px; border-right: 1px solid #ddd">
        <q-list padding>
          <q-item
            to="/"
            exact
            clickable
            v-ripple
          >
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>
            <q-item-section>
              Center
            </q-item-section>
          </q-item>

          <q-item
            to="/mais"
            exact
            clickable
            v-ripple
          >
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>
            <q-item-section>
              Mais
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img class="absolute-top" src="src/assets/imagens/02.png" style="height: 185px">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="src/assets/imagens/01.jpg">
          </q-avatar>
          <div class="text-weight-bold">Gerson</div>
          <div>Aplicativo</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import { date } from 'quasar'

const linksList = [
  {
    title: 'Docs',
    caption: 'gerson',
    icon: 'school',
    link: ''
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
]

export default defineComponent({
  name: 'MainLayout',
  setup() {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  },
  computed: {
    todaysDate() {
      const timeStamp = Date.now()
      return date.formatDate(timeStamp, 'dddd - D - MMMM')
    }
  }
})
</script>

<style scoped>
.header-content {
  text-align: center;
  padding: 2rem 0;
}

.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.2;
  filter: grayscale(100%);
}
</style>

