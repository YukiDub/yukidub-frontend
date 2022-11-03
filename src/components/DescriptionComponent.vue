<template>
  <div class="full-description">
    <p>Описание:</p>
    <ul class="nav nav-pills mb-3">
      <li class="nav-item" role="presentation" @click="selected = 'ru'">
        <button class="nav-link" v-bind:class="{'active': selected === 'ru'}">русское</button>
      </li>
      <li class="nav-item" role="presentation" @click="selected = 'en'">
        <button class="nav-link" v-bind:class="{'active': selected === 'en'}">английское</button>
      </li>
    </ul>
      <div v-if="selected === 'ru'">
        <p class="text">{{ru}}</p>
        <p>Автор:
          <a v-if="ru_author" :href="ru_url" class="author" target=»_blank>{{ru_author}}</a>
          <a v-else class="author">Автор неизвестен</a>
        </p>
      </div>

      <div v-else>
        <p class="text">{{en}}</p>
        <p>Автор:
          <a v-if="en_author" :href="en_url" class="author" target=»_blank>{{en_author}}</a>
          <a v-else class="author">Автор неизвестен</a>
        </p>
      </div>
  </div>
</template>

<script>
import {mapGetters} from 'vuex'
export default {
  name: "DescriptionComponent",
  props: {
    en: String,
    en_author: String,
    en_url: String,
    ru: String,
    ru_url: String,
    ru_author: String,
  },
  data() {
    return {
      selected: 'ru'
    }
  },
  computed: mapGetters(['getLocale']),
}
</script>

<style scoped>
.full-description .text {
  height: 168px;
  overflow-x: hidden;
  overflow-y: scroll;
}
.full-description .tab-pane {
  min-height: 230px;
}
</style>