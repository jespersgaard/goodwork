<template>
  <div class="flex flex-col mx-4 md:mx-auto my-8 max-w-md">
    <template v-if="user.id === authUser.id">
      <div class="bg-white rounded shadow flex flex-row text-center text-grey-darker">
        <div @click="activateTab('profile')" class="w-1/2 p-4" :class="[(activeTab === 'profile') ? 'text-white bg-teal-light' : 'cursor-pointer']">
          Profile
        </div>
        <div @click="activateTab('account')" class="w-1/2 p-4" :class="[(activeTab === 'account') ? 'text-white bg-teal-light' : 'cursor-pointer']">
          Account
        </div>
      </div>
      <account v-if="activeTab === 'account'" :user="authUser"></account>
      <own v-if="activeTab === 'profile'" :user="authUser"></own>
    </template>
    <other v-else :user="user"></other>
  </div>
</template>

<script>
import Account from './account'
import Own from './own'
import Other from './other'
export default {
  components: {Account, Own, Other},
  props: ['user'],
  data: () => ({
    activeTab: 'profile',
    authUser: navbar.user
  }),
  methods: {
    activateTab (tab) {
      this.activeTab = tab
    }
  }
}
</script>
