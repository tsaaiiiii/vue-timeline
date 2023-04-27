<template>
  <div class="timeline">
    <ul class="events">
      <li v-for="(item, index) in events" :key="index">
        <div class="circleClick" @click="showDialog(index)">
          <div class="marker"></div>
        </div>
        <div class="content">
          <div class="line"></div>
          <div class="text">
            <h2>{{ item.year }}</h2>
            <p>{{ item.content }}</p>
          </div>
        </div>
      </li>
    </ul>
    <div v-if="selectedEvent !== null" class="dialog">
      <DialogBox>
        <template #DialogText>
          <span>💡</span>
          <h3>{{ events[selectedEvent].description }}</h3>
        </template>
        <template #DialogButton>
          <input type="button" value="OK!" class="dialogBtn" @click="okBtn" />
          <input type="button" value="更多" class="dialogBtn" @click="moreBtn(selectedEvent)" />
        </template>
      </DialogBox>
    </div>
  </div>
</template>

<script>
import DialogBox from '@/components/DialogBox.vue'
export default {
  data() {
    return {
      events: [
        {
          year: '700AD',
          content: '你知道為什麼吃醋是吃醋，為什麼不是吃其他東西？',
          link: 'https://www.greenconut.com/trivia/jealous-vinegar_1106/',
          description:
            '誰是中國史上吃醋第一人，為什麼爭風吃醋這個現象稱為吃醋，而不是吃別的呢......'
        },
        {
          year: '1166AD',
          content: '你知道以前沒有立可白的時候，寫錯字怎麼辦嗎？',
          link: 'https://www.greenconut.com/trivia/chinese-whiteout_1001/',
          description: '最普遍的方法是，在錯別字旁用毛筆加點，還有一種方法是......'
        },
        {
          year: '1750AD',
          content: '你知道以前沒有鬧鐘的時候，要怎麼起床？',
          link: 'https://www.greenconut.com/trivia/knocker-uppers-alarm-clock_0116/',
          description: '舊世紀的歐洲，鬧鐘是一群拿著長竿的人，稱為敲門人......'
        },
        {
          year: '1979AD',
          content: '你知道麥當勞雞塊，原本是拿來告白用的嗎？',
          link: 'https://www.greenconut.com/trivia/mcdonald-mcnuggets-trivia_0306/',
          description: '麥克雞塊誕生於1979年，雞塊有四種形狀......'
        }
      ],
      selectedEvent: null
    }
  },

  methods: {
    showDialog(index) {
      this.selectedEvent = index
    },
    okBtn() {
      this.selectedEvent = null
    },
    moreBtn(index) {
      window.open(this.events[index].link, '_blank')
      this.selectedEvent = null
    }
  },
  components: {
    DialogBox
  }
}
</script>

<style scoped>
.timeline {
  position: relative;
  display: flex;
  align-items: flex-start;
  margin: 80px;
  max-width: 100%;
}
.events {
  list-style: none;
  margin: 0;
  padding: 0;
  width: 100%;
}

li {
  position: relative;
  display: flex;
  align-items: center;
  margin-bottom: 50px;
  justify-content: center;
}
.circleClick {
  position: relative;
  width: 24px;
  height: 24px;
  border-radius: 100%;
  border: solid 2px #01b468;
  cursor: pointer;
}
.marker {
  position: absolute;
  border: solid 1px white;
  width: 2px;
  min-height: 300px;
  top: -80px;
  left: 8px;
  z-index: 100;
}
.content {
  width: 100%;
  display: flex;
  align-items: center;
}
.line {
  height: 2px;
  width: 60px;
  background-color: white;
  display: flex;
}
.text {
  width: 70%;
  margin-left: 20px;
}
h3 {
  color: black;
}
span {
  font-size: 36px;
}
.dialog {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: white;
  padding: 24px;
  border-radius: 5px;
  text-align: center;
}

input.dialogBtn {
  width: 15%;
  height: 30px;
  border: solid 1px black;
  margin: 20px 10px 10px 10px;
  outline: none;
  background-color: white;
  color: black;
  font-size: 16px;
}
input.dialogBtn:hover {
  background-color: #01b468;
  color: #fff;
  transition-duration: 0.4s;
  font-weight: bold;
}
</style>
