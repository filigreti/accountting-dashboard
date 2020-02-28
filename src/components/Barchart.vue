<template>
  <main>
    <div class="mini-graph">
      <div class="d-flex justify-content-between">
        <div class="title">
          Last Costs
        </div>
        <div class="d-flex legend">
          <div class="d-flex align-items-center mr-3">
            <div class="orange mr-1"></div>
            arrival
          </div>
          <div class="d-flex align-items-center">
            <div class="blue mr-1"></div>
            spending
          </div>
        </div>
      </div>
      <div class="d-flex">
        <div class="line">
          <div class="bar-num">$200</div>
          <div class="bar-num">$100</div>
        </div>
        <div class="mini-graph-bars">
          <div class="bar bar-1" :style="`height:${loopRandom + 6}%;`">
            <div
              class="bar bar-inner"
              :style="`height:${loopRandom + 12}%;`"
            ></div>
            <span>APR</span>
          </div>

          <div class="bar bar-2" :style="`height:${loopRandom2}%;`">
            <div
              class="bar bar-inner"
              :style="`height:${loopRandom + 4}%;`"
            ></div>
            <span>MAY</span>
          </div>

          <div class="bar bar-3" :style="`height:${loopRandom4 - 7}%;`">
            <div
              class="bar bar-inner"
              :style="`height:${loopRandom - 3}%;`"
            ></div>
            <span>JUNE</span>
          </div>

          <div class="bar bar-4" :style="`height:${loopRandom3 - 7}%;`">
            <div class="bar bar-inner" :style="`height:${loopRandom}%;`"></div>
            <span>JULY</span>
          </div>

          <div class="bar bar-5" :style="`height:${loopRandom5}%;`">
            <div
              class="bar bar-inner"
              :style="`height:${loopRandom4 - 16}%;`"
            ></div>
            <span>AUG</span>
          </div>

          <div class="bar bar-6" :style="`height:${loopRandom + 18}%;`">
            <div class="bar bar-inner" :style="`height:${loopRandom3}%;`"></div>
            <span>SEP</span>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      loopRandom: 23,
      loopRandom2: 56,
      loopRandom3: 39,
      loopRandom4: 47,
      loopRandom5: 39
    };
  },

  methods: {
    randomHeight(min, max) {
      return Math.floor(Math.random() * (max - min + 1)) + min;
    }
  },
  mounted() {
    setInterval(() => {
      this.loopRandom = this.randomHeight(5, 35);
      this.loopRandom2 = this.randomHeight(56, 60);
      this.loopRandom3 = this.randomHeight(15, 58);
      this.loopRandom4 = this.randomHeight(37, 60);
      this.loopRandom5 = this.randomHeight(8, 68);
    }, 10000);
  }
};
</script>

<style scoped>
.mini-graph-bars {
  background: inherit;
  position: relative;
  height: 83px;
  width: 140px;
  margin-left: 30px;
}
.mini-graph-bars .bar {
  background: transparent linear-gradient(180deg, #00c6ff 0%, #0072ff 100%) 0%
    0% no-repeat padding-box;
  width: 20px;
}
.mini-graph-bars .bar:nth-of-type(2) {
  left: 28px;
}
.mini-graph-bars .bar:nth-of-type(3) {
  left: 56px;
}
.mini-graph-bars .bar:nth-of-type(4) {
  left: 84px;
}
.mini-graph-bars .bar:nth-of-type(5) {
  left: 112px;
}
.mini-graph-bars .bar:nth-of-type(6) {
  left: 140px;
}
.mini-graph-bars .bar:nth-of-type(7) {
  left: 168px;
}
.mini-graph-bars .bar:nth-of-type(8) {
  left: 196px;
}
.mini-graph-bars .bar:nth-of-type(9) {
  left: 224px;
}
.mini-graph-bars .bar-inner {
  background: transparent linear-gradient(180deg, #fe6dad 0%, #fc9f35 100%) 0%
    0% no-repeat padding-box;
}
.mini-graph-bars .bar {
  position: absolute;
  bottom: 0;
}
.mini-graph span {
  color: #a6a9b7;
  font-size: 10px;
  position: absolute;
  bottom: -25px;
}
.line {
  width: 100%;
  height: 83px;
  position: absolute;
  z-index: 2;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 20px 0 15px;
}
.bar-num {
  font-size: 8px;
  color: #a6a9b7;
  position: relative;
  display: flex;
  align-items: center;
}
.bar-num::before {
  content: '';
  position: absolute;
  width: 70%;
  left: 25px;
  height: 1px;
  border: 0.5px dashed #a6a9b7;
  z-index: 4;
}
.legend div {
  font-size: 10px;
}
.blue {
  height: 3px;
  width: 3px;
  background: linear-gradient(180deg, #00c6ff 0%, #0072ff 100%);
  border-radius: 50%;
}
.orange {
  height: 3px;
  width: 3px;
  background: linear-gradient(180deg, #fe6dad 0%, #fc9f35 100%);
  border-radius: 50%;
}
</style>
