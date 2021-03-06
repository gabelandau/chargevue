<!--

filename: Committee.vue
description: Page for viewing charges assigned to specific committees

author: Gabe Landau <gll1872@rit.edu>

-->

<template>
  <div class="dashboard">
    <HeaderMenu />
    <CommitteesMenu />
    <div class="pagename">
      <h1>{{ committee.description }}</h1>
    </div>
    <CommitteeOverview inProgressCount="1" incompleteCount="3" completedCount="10" indefiniteCount="3" stoppedCount="2" />
    <h1 id="active_projects_title">Active Projects</h1>
    <h2>Projects that have been recently updated.</h2>
    <ProjectThumbnail />
    <h1>Projects In Progress</h1>
    <h2>Projects that are currently in progress.</h2>
    <ProjectThumbnail />
    <ProjectThumbnail />
    <h1>Projects Completed</h1>
    <h2>Projects that have been completed.</h2>
    <div class="columns">
      <div class="column"><ProjectThumbnailSmall /></div>
      <div class="column"><ProjectThumbnailSmall /></div>
      <div class="column"><ProjectThumbnailSmall /></div>
    </div>
    <div class="columns">
      <div class="column"><ProjectThumbnailSmall /></div>
      <div class="column"><ProjectThumbnailSmall /></div>
      <div class="column"><ProjectThumbnailSmall /></div>
    </div>
  </div>
</template>

<script>
import CommitteeInfo from '../mixins/committeeinfo'
import HeaderMenu from '../components/HeaderMenu'
import CommitteesMenu from '../components/CommitteesMenu'
import CommitteeOverview from '../components/CommitteeOverview'
import ProjectThumbnail from '../components/ProjectThumbnail'
import ProjectThumbnailSmall from '../components/ProjectThumbnailSmall'

export default {
  name: 'dashboard',
  mixins: [CommitteeInfo],
  components: {
    'HeaderMenu': HeaderMenu,
    'CommitteesMenu': CommitteesMenu,
    'CommitteeOverview': CommitteeOverview,
    'ProjectThumbnail': ProjectThumbnail,
    'ProjectThumbnailSmall': ProjectThumbnailSmall
  },
  data () {
    return {
      committee: {'description': 'committee'}
    }
  },
  sockets: {
    get_committee: function (data) {
      this.committee = data
    }
  },
  beforeMount () {
    this.$socket.emit('get_committee', this.$router.history.current.params['committee'])
  },
  /* Since this component is used for each committee page, we have to
    watch for changes in the URL and update the props on the page
    when the route changes */
  watch: {
    '$route.params.committee': function (committee) {
      this.$socket.emit('get_committee', committee)
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: 300;
  text-align: center;
}

.columns {
  width: 70%;
  margin: 0 auto;
}

.pagename {
    background: #000;
}

.pagename h1 {
  margin: 0;
  text-align: center;
  text-transform: uppercase;
  padding: 75px 0;
  color: #fff;
  animation: fadein 0.5s;
  -webkit-animation: fadein 0.5s;
  -moz-animation: fadein 0.5s;
  -ms-animation: fadein 0.5s;
}


@keyframes fadein {
  from { opacity: 0; }
  to   { opacity: 1; }
}

/* Firefox < 16 */
@-moz-keyframes fadein {
  from { opacity: 0; }
  to   { opacity: 1; }
}

/* Safari, Chrome and Opera > 12.1 */
@-webkit-keyframes fadein {
  from { opacity: 0; }
  to   { opacity: 1; }
}

/* Internet Explorer */
@-ms-keyframes fadein {
  from { opacity: 0; }
  to   { opacity: 1; }
}
</style>
