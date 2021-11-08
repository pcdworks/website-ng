<template>
<v-row
      class="fill-height"
      align="center"
      justify="start"
    >
      <template v-for="(member, id) in members">
        <v-col
          :key="id"
          cols="12"
          md="4"
        >
          <team-member
            :name="member.name"
            :title="member.title"
            :education="member.education"
            :information="member.information"
            :skills="member.skills"
            :linkedin="member.linkedin"
            :twitter="member.twitter"
            :email="member.email"
          ></team-member>
        </v-col>
      </template>
</v-row>
</template>

<script>
import TeamMember from './TeamMember.vue'
export default {
  components: { TeamMember },
  props: {
    members: {
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

</style>