<template>
  <q-layout view="lHh Lpr lFf" style="background-color: #2c0145">
    <!-- HEADER -->
    <q-header elevated>
      <q-toolbar style="background-color: #220036">
        <q-btn flat dense round icon="menu" aria-label="Menu" style="color: #ffffff" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          &nbsp;&nbsp;<a href="/"><img src="/images/logo.png" height="50" style="padding-top: 8px" /></a>
        </q-toolbar-title>

        <q-toolbar-title>
          <q-btn flat color="white" icon="language">
            <q-menu fit dark transition-show="scale" transition-hide="scale">
              <q-list style="min-width: 100px">
                <q-select dark v-model="locale" :options="localeOptions" dense borderless emit-value map-options
                  options-dense style="min-width: 150px; padding: 10px">
                </q-select>
              </q-list>
            </q-menu>
          </q-btn>
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-not-above bordered
      style="background: linear-gradient(to bottom, #2c0145, #31014c)">
      <q-list>
        <q-item-label header style="color: #ffffff">
          {{ $t('drawer.title') }}
        </q-item-label>

        <EssentialLink v-for="link in essentialLinks" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <div style="background: linear-gradient(to bottom, #ffffff, #ffffff)">
      <q-toolbar>
        <q-toolbar-title header style="font-weight: bold; font-size: 15px">
          &nbsp; &nbsp; GamePlace 2023 &nbsp; Abay Ave 2 &nbsp;
          <a href="/" style="color: #000000"><q-icon name="ion-logo-whatsapp" size="sm"></q-icon></a>&nbsp;&nbsp;&nbsp;
          <a href="/" style="color: #000000"><q-icon name="ion-logo-twitter" size="sm"></q-icon></a>&nbsp;&nbsp;&nbsp;
          <a href="/" style="color: #000000"><q-icon name="ion-logo-instagram" size="sm"></q-icon></a>
        </q-toolbar-title>
      </q-toolbar>
    </div>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import { useI18n } from 'vue-i18n'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Instagram',
    icon: 'ion-logo-instagram',
    link: 'https://instagram.com'
  },
  {
    title: 'Twitter',
    icon: 'ion-logo-twitter',
    link: 'https://x.com'
  },
  {
    title: 'WhatsApp',
    icon: 'ion-logo-whatsapp',
    link: 'https://facebook.com'
  }
]

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup() {
    const { locale } = useI18n({ useScope: 'global' })
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },
      locale,
      localeOptions: [
        { value: 'kz', label: 'KZ' },
        { value: 'ru', label: 'RU' },
        { value: 'en-US', label: 'EN' },
      ]
    }
  }
})
</script>

<style>
a {
  text-decoration: none;
  color: #f1df83;
}

a:link {
  text-decoration: none;
  color: #f1df83;
}

a:visited {
  text-decoration: none;
  color: #f1df83;
}

a:hover {
  text-decoration: none;
  color: #f1df83;
}

a:active {
  text-decoration: none;
  color: #f1df83;
}
</style>
