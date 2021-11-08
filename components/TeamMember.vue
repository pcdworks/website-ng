<template>
  <v-card
    elevation="4"
    outlined
    shaped
  >
    <v-card-text>
      <v-list-item class="grow">
        <v-list-item-avatar size="80" tile>
          <v-img
            class="elevation-6"
            :alt="name"
            :src="avatar"
          ></v-img>
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title>{{name}}</v-list-item-title>
          <v-list-item-subtitle>{{title}}</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
      <v-tabs>
        <v-tab v-if="information != ''">Information</v-tab>
        <v-tab v-if="(skills && skills.length != 0) ||
                     (education && education.length != 0)">Education & Skills</v-tab>
        <v-tab-item v-if="information != ''" class="tabby">
          <br/>
          {{information}}
        </v-tab-item>
        <v-tab-item v-if="(skills && skills.length != 0) ||
                          (education && education.length != 0)" class="tabby">
          <br/>
          <h3 v-if="education && education.length != 0">Education</h3>
          <ul>
            <li v-for="(e, id) in education" :key="id">
              {{e}}
            </li>
          </ul>
          <h3 v-if="skills && skills.length != 0">Skills</h3>
          <ul>
            <li v-for="(skill, id) in skills" :key="id">
              {{skill}}
            </li>
          </ul>
        </v-tab-item>
      </v-tabs>
    </v-card-text>
    <v-card-actions>
      <v-spacer/>
      <a v-if="phone != ''" :href="'tel:' + phone" target="_blank" class="mr-1">
        <b-btn icon>
          <v-icon>mdi-phone</v-icon>
        </b-btn>
      </a>
      <a v-if="email != ''" :href="'mailto:' + email" target="_blank" class="mr-1">
        <b-btn icon>
          <v-icon>mdi-email</v-icon>
        </b-btn>
      </a>
      <a v-if="linkedin != ''" :href="linkedin" target="_blank" class="mr-1">
        <b-btn icon>
          <v-icon>mdi-linkedin</v-icon>
        </b-btn>
      </a>
      <a v-if="twitter != ''" :href="twitter" target="_blank" class="mr-1">
        <b-btn icon>
          <v-icon>mdi-twitter</v-icon>
        </b-btn>
      </a>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: '',
    },
    title: {
      type: String,
      default: '',
    },
    email: {
      type: String,
      default: '',
    },
    education: {
      type: Array,
      default: () => { return [] },
    },
    avatar: {
      type: String,
      default: '/images/pcd-simple-512.png',
    },
    linkedin: {
      type: String,
      default: '',
    },
    twitter: {
      type: String,
      default: '',
    },
    information: {
      type: String,
      default: ''
    },
    phone: {
      type: String,
      default: ''
    },
    skills: {
      type: Array,
      default: () => { return [] }
    }
  },
  data: () => {
    return {}
  }
}
</script>

<style>

.tabby {
  height: 180px;
  overflow-y: scroll;
}

</style>