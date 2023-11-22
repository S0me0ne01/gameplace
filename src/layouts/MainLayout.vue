<template>
  <q-layout view="lHh Lpr lFf" style="background-color: #2c0145">
    <!-- HEADER -->
    <q-header elevated>
      <q-toolbar style="background-color: #220036">
        <q-btn flat dense round icon="menu" aria-label="Menu" style="color: #ffffff" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          &nbsp;&nbsp;<a href="/"><img src="/images/logo.png" height="50" style="padding-top: 8px" /></a>
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-not-above bordered
      style="background: linear-gradient(to bottom, #2c0145, #31014c)">
      <q-list>
        <q-item-label header style="color: #ffffff">
          Полезные ссылки
        </q-item-label>

        <EssentialLink v-for="link in essentialLinks" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <div style="background: linear-gradient(to bottom, #2c0145, #31014c); color: white">
      <q-toolbar>
        <q-toolbar-title header style="font-weight: bold">
          &nbsp; &nbsp; Coffee | 2023 | Abay Ave 2 &nbsp;
          <a href="/" style="color: #3dd10c"><q-icon name="ion-logo-whatsapp" size="md"></q-icon>&nbsp;&nbsp;&nbsp;</a>
          <a href="/" style="color: #0ed1db"><q-icon name="ion-logo-twitter" size="md"></q-icon>&nbsp;&nbsp;&nbsp;</a>
          <a href="/" style="color: #bc0edb"><q-icon name="ion-logo-instagram" size="md"></q-icon></a>
        </q-toolbar-title>
      </q-toolbar>
    </div>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Instagram',
    icon: 'ion-logo-instagram',
    caption: 'Ещё больше фото здесь',
    link: 'https://instagram.com'
  },
  {
    title: 'Twitter',
    caption: 'Наш аккаунт в Twitter',
    icon: 'ion-logo-twitter',
    link: 'https://x.com'
  },
  {
    title: 'WhatsApp',
    caption: 'Мы в WhatsApp',
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
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
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
