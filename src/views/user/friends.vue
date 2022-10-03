<template>
  <div class="friends-page">
    <div class="header">
      <p class="button back" v-on:click="$router.go(-1)"><i class="bi bi-arrow-left-short"></i>вернуться назад</p>
      <p class="p-title">Все пользователи</p>
    </div>
    <div class="content entry-list">
      <div class="friend" v-for="user in users.slice(0, 20)" :key="user.id" :title="user.name">
        <img class="avatar" src="/assets/images/avatars/default.png" :alt="user.name">
        <div class="text-center">
          <router-link :to="{name: 'user.profile', params: {name: user.name}}">{{user.name}}</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "friends",
  data(){
    return {
      user: {
        id: 1,
        name: this.$route.params.name,
        avatar_url: '/assets/images/avatars/default.png',
      },
      users: [
        {
          id: 1,
          name: "test 1",
          avatar_url: '/assets/images/avatars/default.png',
        },
        {
          id: 2,
          name: "test 2",
          avatar_url: '/assets/images/avatars/default.png',
        },
        {
          id: 3,
          name: "test 3",
          avatar_url: '/assets/images/avatars/default.png',
        }
      ]
    }
  }
}
</script>

<style scoped>
.friends-page > .header{
  display: flex;
  align-items: center;
}
.friends-page > .header > .button.back{
  cursor: pointer;
  font-size: 1rem;
  flex: 1;
}
.friends-page > .header > .title{
  font-family: IBM Plex Sans;
  text-transform: uppercase;
  font-size: 18px;
  line-height: 23px;
  flex: 1;
}
.friends-page>.content{
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  padding: 12px;
  overflow: hidden;
}
.friends-page>.content .friend > .avatar{
  flex: 1 1 auto;
  width: 120px;
}
</style>