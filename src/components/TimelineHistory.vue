<template>
  <div class="timeline">
    <!-- <ul class="events">
      <li v-for="(item, index) in history" :key="index">
        <div class="blank"><div class="marker" @click="showDialog(index)"></div></div>
        <div class="content">
          <div class="line"></div>
          <div class="text">
            <h2>{{ item.year }}</h2>
            <p>{{ item.thing }}</p>
          </div>
        </div>
      </li>
    </ul> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      history: [
        {
          year: '',
          thing: '',
          description: ''
        }
      ],
      selectedEvent: null
    }
  },
  methods: {
    showDialog(index) {
      this.selectedEvent = index
    }
  },
  components: {}
}
</script>
