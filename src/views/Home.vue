<template>
  <main class="home d-flex">
    <div class="left-home">
      <div class="d-flex justify-content-between d-flex align-items-start h-100">
        <div class="home-top d-flex align-items-center">
          <div class="link-bottom-text welcome">Welcome</div>
          <div class="overview">Overview</div>
        </div>
        <div>
          <img src="@/assets/bxs-bell.svg" style="height:16px" alt />
        </div>
      </div>

      <div class="grid">
        <div class="card-cont">
          <div class="credit-card box d-flex flex-column justify-content-between">
            <img src="@/assets/waves.svg" class="waves" alt />
            <img src="@/assets/visa.svg" style="width:45px" alt />
            <div class="d-flex align-items-center">
              <div>
                <img v-for="i in 4" :key="i" src="@/assets/asterix.svg" alt />
              </div>
              <div class="ml-2">
                <img v-for="i in 4" :key="i" src="@/assets/asterix.svg" alt />
              </div>
              <div class="ml-2">
                <img v-for="i in 4" :key="i" src="@/assets/asterix.svg" alt />
              </div>
              <div class="ml-2 card-num">4765</div>
            </div>
            <div>
              <div class="d-flex justify-content-between">
                <div class="card-num-light">CARD HOLDER</div>
                <div class="card-num-light">VALID THRU</div>
              </div>
              <div class="d-flex justify-content-between">
                <div class="card-num-person">Stephen Austin</div>
                <div class="card-num-person">07/22</div>
              </div>
            </div>
          </div>
          <div class="blur"></div>
        </div>

        <div class="box line-chart">
          <linechart />
        </div>
        <div class="box line-chart">
          <barchart />
        </div>
      </div>
      <div class="grid-two">
        <div class="bottom-one">
          <div class="bottom-one-header">
            <div>Income</div>
            <img src="@/assets/three-dot.svg" alt />
          </div>
          <div id="table-one" class="table-grid mb-3">
            <div>
              <div class="text-center table-head">#</div>
            </div>
            <div>
              <div class="text-center table-head">Name</div>
            </div>
            <div>
              <div class="text-right table-head">Amount</div>
            </div>
            <div>
              <div class="text-right table-head">Date</div>
            </div>
            <div></div>
          </div>
          <div
            v-for="(person, index) in sortedArray.slice(0, 7)"
            :key="person.id"
            class="table-grid border-bottom"
            :class="{ 'active-hove ': check.includes(index) }"
          >
            <div class="d-flex justify-content-center align-items-center only">
              <input type="checkbox" name :id="person.id" :value="index" v-model="check" />
              <div class="pl-2">DC0{{ index + 1 }}</div>
            </div>
            <div class="d-flex justify-content-between align-items-center only px-3">
              <!-- <img :src="person.download_url" alt /> -->
              <img src="@/assets/person.png" alt />
              <div class="pl-2 table-head">{{ person.author | truncate(10, '...') }}</div>
            </div>
            <div class="d-flex justify-content-end align-items-center only">
              <div>${{ person.height }}</div>
            </div>
            <div class="d-flex justify-content-end align-items-center only">
              <div>{{ person.date }}</div>
            </div>
            <div class="d-flex justify-content-end align-items-center only">
              <div
                v-if="!check.includes(index)"
                :style="
                  `width:5px;height:5px;background:${person.color}; border-radius:50%; margin-right:10px`
                "
              ></div>
              <div class="d-flex" style="margin-right:10px" v-else>
                <div class="mr-3">
                  <svg
                    width="15"
                    height="15"
                    viewBox="0 0 20 20"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M19 13V17C19 17.5304 18.7893 18.0391 18.4142 18.4142C18.0391 18.7893 17.5304 19 17 19H3C2.46957 19 1.96086 18.7893 1.58579 18.4142C1.21071 18.0391 1 17.5304 1 17V13"
                      stroke="white"
                      stroke-width="2"
                      stroke-miterlimit="10"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                    <path
                      d="M5 8L10 13L15 8"
                      stroke="white"
                      stroke-width="2"
                      stroke-miterlimit="10"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                    <path
                      d="M10 13V1"
                      stroke="white"
                      stroke-width="2"
                      stroke-miterlimit="10"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                  </svg>
                </div>
                <div>
                  <svg
                    width="5"
                    height="18"
                    viewBox="0 0 5 18"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M2.03196 13.936C2.43386 13.936 2.82672 14.0552 3.16088 14.2785C3.49504 14.5017 3.75549 14.8191 3.90929 15.1904C4.06308 15.5617 4.10332 15.9703 4.02492 16.3644C3.94651 16.7586 3.75299 17.1207 3.4688 17.4048C3.18462 17.689 2.82256 17.8826 2.42839 17.961C2.03422 18.0394 1.62565 17.9991 1.25435 17.8453C0.883052 17.6915 0.565697 17.4311 0.342418 17.0969C0.119139 16.7628 -3.62396e-05 16.3699 -3.62396e-05 15.968C-3.62396e-05 15.4291 0.214049 14.9122 0.595123 14.5312C0.976197 14.1501 1.49304 13.936 2.03196 13.936ZM2.03196 6.968C2.43386 6.968 2.82672 7.08717 3.16088 7.31045C3.49504 7.53373 3.75549 7.85109 3.90929 8.22239C4.06308 8.59369 4.10332 9.00225 4.02492 9.39642C3.94651 9.79059 3.75299 10.1527 3.4688 10.4368C3.18462 10.721 2.82256 10.9146 2.42839 10.993C2.03422 11.0714 1.62565 11.0311 1.25435 10.8773C0.883052 10.7235 0.565697 10.4631 0.342418 10.1289C0.119139 9.79476 -3.62396e-05 9.40189 -3.62396e-05 9C-3.62396e-05 8.46108 0.214049 7.94423 0.595123 7.56316C0.976197 7.18209 1.49304 6.968 2.03196 6.968ZM2.03196 0C2.43386 0 2.82672 0.119175 3.16088 0.342454C3.49504 0.565733 3.75549 0.883088 3.90929 1.25439C4.06308 1.62569 4.10332 2.03425 4.02492 2.42842C3.94651 2.82259 3.75299 3.18466 3.4688 3.46884C3.18462 3.75302 2.82256 3.94655 2.42839 4.02496C2.03422 4.10336 1.62565 4.06312 1.25435 3.90932C0.883052 3.75553 0.565697 3.49508 0.342418 3.16092C0.119139 2.82676 -3.62396e-05 2.43389 -3.62396e-05 2.032C-3.62396e-05 1.49308 0.214049 0.976233 0.595123 0.595159C0.976197 0.214085 1.49304 0 2.03196 0V0Z"
                      fill="white"
                    />
                  </svg>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="bottom-two">
          <div class="bottom-one-header">
            <div>Monthly Profit</div>
            <img src="@/assets/three-dot.svg" alt />
          </div>
          <dougnut />
          <div
            style="padding:20px 20px; font-size:11px"
            class="d-flex justify-content-between mt-2"
          >
            <div>{{ moment }}</div>
          </div>
          <div
            v-for="i in 4"
            style="padding:7px 20px; "
            :key="i"
            class="border-bottom d-flex flex-column justify-content-between"
          >
            <div class="d-flex align-item-center">
              <div>
                <svg
                  width="30"
                  height="30"
                  viewBox="0 0 42 42"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    d="M21 42C32.598 42 42 32.598 42 21C42 9.40202 32.598 0 21 0C9.40202 0 0 9.40202 0 21C0 32.598 9.40202 42 21 42Z"
                    fill="url(#paint0_linear)"
                  />
                  <path
                    d="M23.573 24.738C23.857 24.738 24.1346 24.6538 24.3707 24.4961C24.6068 24.3383 24.7909 24.1141 24.8996 23.8518C25.0083 23.5894 25.0368 23.3007 24.9815 23.0222C24.9261 22.7437 24.7895 22.4878 24.5888 22.2869C24.388 22.0861 24.1322 21.9492 23.8538 21.8937C23.5753 21.8382 23.2866 21.8665 23.0242 21.975C22.7617 22.0836 22.5374 22.2675 22.3795 22.5035C22.2216 22.7395 22.1372 23.017 22.137 23.301C22.138 23.6816 22.2896 24.0464 22.5587 24.3156C22.8277 24.5848 23.1924 24.7367 23.573 24.738Z"
                    fill="white"
                  />
                  <path
                    d="M29.32 29.046H15.673C15.2001 29.0511 14.7309 28.9617 14.293 28.7831C13.8551 28.6045 13.4573 28.3403 13.1228 28.0059C12.7883 27.6715 12.524 27.2738 12.3453 26.8359C12.1666 26.398 12.077 25.9289 12.082 25.456V16.119C12.0828 15.3573 12.3857 14.627 12.9244 14.0884C13.463 13.5497 14.1933 13.2468 14.955 13.246H27.882V16.119H26.447V14.682H14.955C14.574 14.682 14.2086 14.8333 13.9392 15.1027C13.6698 15.3721 13.5185 15.7375 13.5185 16.1185C13.5185 16.4995 13.6698 16.8649 13.9392 17.1343C14.2086 17.4037 14.574 17.555 14.955 17.555H29.32V29.046ZM13.518 18.56V25.46C13.5114 25.7448 13.5627 26.028 13.6687 26.2924C13.7746 26.5568 13.9331 26.797 14.1346 26.9984C14.336 27.1999 14.5762 27.3584 14.8406 27.4643C15.105 27.5703 15.3882 27.6216 15.673 27.615H27.882V18.992H14.955C14.4437 18.9939 13.9435 18.8435 13.518 18.56Z"
                    fill="white"
                  />
                  <defs>
                    <linearGradient
                      id="paint0_linear"
                      x1="21"
                      y1="0"
                      x2="21"
                      y2="42"
                      gradientUnits="userSpaceOnUse"
                    >
                      <stop stop-color="#00C6FF" />
                      <stop offset="1" stop-color="#0072FF" />
                    </linearGradient>
                  </defs>
                </svg>
              </div>
              <div class="ml-2">
                <div class="dough-card">Card **** **** **** 5678</div>
                <div class="dough-card-light">5 march, 18:33</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="right-home">
      <div>
        <img src="@/assets/person.png" class="img-fluid person" alt />
        <span class="person-name">Ingredia Nutrisha</span>
        <svg
          class="drop-down ml-5"
          width="10"
          height="5"
          viewBox="0 0 10 5"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M4.76194 4.818C4.79324 4.84935 4.83042 4.87423 4.87135 4.8912C4.91227 4.90817 4.95614 4.91691 5.00044 4.91691C5.04475 4.91691 5.08862 4.90817 5.12954 4.8912C5.17047 4.87423 5.20764 4.84935 5.23894 4.818L9.48094 0.575C9.52795 0.527872 9.55996 0.467877 9.57291 0.402583C9.58587 0.337289 9.57919 0.269621 9.55373 0.208115C9.52828 0.146609 9.48517 0.09402 9.42986 0.056982C9.37455 0.0199441 9.30951 0.000116362 9.24294 0H0.756943C0.690377 0.000116362 0.625336 0.0199441 0.570024 0.056982C0.514713 0.09402 0.47161 0.146609 0.446152 0.208115C0.420694 0.269621 0.414021 0.337289 0.426976 0.402583C0.43993 0.467877 0.471932 0.527872 0.518943 0.575L4.76194 4.818Z"
            fill="#43424B"
          />
        </svg>
      </div>
      <div class="grid-right">
        <div class="right-one">
          <div class="title d-flex justify-content-between ini-space">
            Payment History
            <img src="@/assets/three-dot.svg" alt />
          </div>
          <div
            v-for="(data, index) in history"
            style="padding:9px 12px; "
            :key="index"
            class="border-bottom d-flex flex-column"
          >
            <div class="d-flex align-items-center justify-content-between">
              <div class="d-flex align-items-center">
                <div>
                  <img class="img-right" :src="data.icon" alt />
                </div>
                <div class="ml-2">
                  <div class="dough-card">{{ data.text }}</div>
                  <div class="dough-card-light">5 march, 18:33</div>
                </div>
              </div>
              <div class="d-flex flex-column justify-content-end align-items-end">
                <div
                  style="font-size:12px"
                  :class="data.number >= 0 ? 'success' : 'danger'"
                >{{ data.number > 0 ? '+' + data.number : data.number }}</div>
                <div style="font-size:9px; color:#A6A9B7">USD</div>
              </div>
            </div>
          </div>
        </div>
        <div class="right-two">
          <div class="title d-flex justify-content-between ini-space">
            Recent Reviews
            <img src="@/assets/three-dot.svg" alt />
          </div>
          <div
            style="padding:9px 12px;font-size:12px "
            class="d-flex align-items-center border-bottom pb-3"
          >
            <span style="border-radius:4px" class="border px-2 py-1">4.3</span>
            <star-rating
              class="ml-2 mb-1"
              :star-size="12"
              :show-rating="false"
              :rating="4"
              active-color="#FD866F"
            ></star-rating>
            <div class="ml-2" style="font-sixe:12px">360 Reviews</div>
          </div>
          <div v-for="i in 1" :key="i" style="padding:9px 12px;font-size:12px " class="d-flex">
            <img class="last-img" src="@/assets/person.png" alt />
            <div class="ml-2 mt-2">
              <div>Belle Brown</div>
              <star-rating
                class
                :star-size="12"
                :show-rating="false"
                :rating="4"
                active-color="#FD866F"
              ></star-rating>
              <div>
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
                Reprehenderit eaque velit vero tenetur iure quis, nobis totam
              </div>
              <div class="d-flex mt-2">
                <svg
                  width="17"
                  height="17"
                  viewBox="0 0 20 17"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    d="M7.778 4.444V0L0 7.778L7.778 15.556V11C13.334 11 17.222 12.778 20 16.667C18.889 11.111 15.556 5.556 7.778 4.444Z"
                    fill="url(#paint0_linear)"
                  />
                  <defs>
                    <linearGradient
                      id="paint0_linear"
                      x1="10"
                      y1="0"
                      x2="10"
                      y2="16.667"
                      gradientUnits="userSpaceOnUse"
                    >
                      <stop stop-color="#00C6FF" />
                      <stop offset="1" stop-color="#0072FF" />
                    </linearGradient>
                  </defs>
                </svg>
                <div style="color: #A6A9B7;opacity: 1; font-size:10px" class="pl-2">Reply</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import linechart from "../components/Linechart";
import barchart from "../components/Barchart";
import dougnut from "../components/Dougnut";
import moment from "moment";
import reload from "../assets/reload.svg";
import paypal from "../assets/Paypal.svg";
import tick from "../assets/tick.svg";
import cancel from "../assets/cancel.svg";
import refund from "../assets/refund.svg";

export default {
  data() {
    return {
      persons: "",
      active: false,
      check: [1],
      moment: moment().format("MM/DD/YYYY"),
      history: [
        { icon: reload, text: "Depost From ATL", number: -1470 },
        {
          icon: paypal,
          text: "Deposit Paypal",
          number: +2220
        },
        {
          icon: tick,
          text: "Deposit from ATL",
          number: +250
        },
        {
          icon: cancel,
          text: "Cancelled",
          number: 0
        },
        {
          icon: refund,
          text: "Refund",
          number: -950
        }
      ]
    };
  },
  components: {
    linechart,
    barchart,
    dougnut
  },
  watch: {
    check(x) {
      console.log(x);
    }
  },
  computed: {
    sortedArray() {
      let value1 = `transparent linear-gradient(180deg, #00C6FF 0%, #0072FF 100%) 0% 0% no-repeat padding-box`;
      let value2 = `transparent linear-gradient(180deg, #FE6DAD 0%, #FC9F35 100%) 0% 0% no-repeat padding-box;`;
      if (this.persons)
        this.persons.map(x => {
          return (
            (x.date = this.randomDate()),
            (x.color = Math.random() < 0.5 ? value1 : value2)
          );
        });
      return this.persons;
    }
  },
  filters: {
    truncate: function(text, length, suffix) {
      return text.substring(0, length) + suffix;
    }
  },
  methods: {
    randomDate() {
      return moment(
        new Date(+new Date() - Math.floor(Math.random() * 10000000000))
      ).format("MM/DD/YYYY");
    }
  },
  async mounted() {
    let res = await fetch("https://picsum.photos/v2/list");
    this.persons = await res.json();
  }
};
</script>

<style scoped>
.welcome {
  font-size: 1rem;
  color: inherit;
}

.overview {
  font-size: 0.8rem;
  margin-left: 3rem;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.overview::before {
  position: absolute;
  content: "";
  background: #43424b;
  width: 50%;
  height: 2px;
  top: 20px;
}

.left-home {
  flex: 9.3;
  height: 100vh;
  margin-right: 1rem;
  height: 40px;
  background: inherit;
}

.right-home {
  flex: 3.3;
  margin-right: 0.8rem;
  height: 40px;
  align-items: center;
  background: inherit;
}

.person {
  height: 35px;
  width: 35px;
  object-fit: cover;
  border-radius: 50%;
}

.person-name {
  font-size: 12px;
  margin-left: 0.8rem;
  font-weight: 500;
}

.grid {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.8rem;
  margin-top: 20px;
}

.box {
  height: 150px;
  border-radius: 10px;
  position: relative;
}

.credit-card {
  background: transparent linear-gradient(121deg, #8500f9 0%, #e70eff 100%) 0%
    0% no-repeat padding-box;
  overflow: hidden;
  z-index: 2;
  padding: 12px 10px;
}

.waves {
  position: absolute;
  opacity: 0.6;
  left: -100px;
  top: 20px;
}

.card-cont {
  position: relative;
  z-index: 1;
  width: 100%;
}

.blur {
  position: absolute;
  width: 90%;
  height: 120px;
  background: transparent linear-gradient(90deg, #8500f9 0%, #e70eff 100%) 0% 0%
    no-repeat padding-box;
  border-radius: 8px;
  opacity: 0.26;
  filter: blur(30px);
  z-index: -5;
  top: 50px;
  left: 10px;
}

.card-num {
  font-size: 14px;
  color: white;
  margin-top: 4px;
}

.card-num-light {
  font-size: 9px;
  opacity: 0.6;
  color: white;
}

.card-num-person {
  font-size: 10px;
  color: white;
}

.line-chart {
  background: inherit;
  box-shadow: 0px 10px 25px #00000008;
  border: 0.5px solid #e8e8e8;
  border-radius: 10px;
  opacity: 1;
  padding: 12px 10px 10px;
  width: 100%;
}

.grid-two {
  display: grid;
  grid-template-columns: 2.05fr 1fr;
  gap: 0.8rem;
  margin-top: 0.8rem;
}

.grid-two .bottom-one,
.bottom-two {
  height: calc(100vh - 255px);
  background: inherit 0% 0% no-repeat padding-box;
  box-shadow: 0px 10px 25px #00000008;
  border: 0.5px solid #e8e8e8;
  border-radius: 10px;
  opacity: 1;
  overflow-y: auto;
}
.bottom-two {
  position: relative;
}
.bottom-one-header {
  display: flex;
  justify-content: space-between;
  padding: 20px 20px;
  background: inherit;
  position: sticky;
  top: 0;
  width: 100%;
  font-size: 12px;
  font-weight: bold;
}
.table-grid {
  display: grid;
  grid-template-columns: 2fr 3.2fr 1.5fr 2.2fr 1.8fr;
}
.table-head {
  font-size: 12px;
  font-weight: 500;
}
.table-grid img {
  width: 30px;
  height: 30px;
  object-fit: cover;
  border-radius: 4px;
  filter: blur(8);
}
.last-img {
  width: 35px;
  height: 35px;
  object-fit: cover;
  border-radius: 50%;
  filter: blur(8);
}
.only {
  font-size: 12px;
  padding: 10px 0;
}
.active-hover:hover {
  background: transparent linear-gradient(92deg, #fe6dad 0%, #fc9f35 100%) 0% 0%
    no-repeat padding-box;
  box-shadow: 0px 0px 44px #31389608;
}
.active-hove {
  background: transparent linear-gradient(92deg, #fe6dad 0%, #fc9f35 100%) 0% 0%
    no-repeat padding-box;
  box-shadow: 0px 0px 44px #31389608;
  color: white;
  border: none;
}
.dough-card {
  font-size: 12px;
  font-weight: bold;
  color: inherit;
}
.dough-card-light {
  color: inherit;
  font-size: 10px;
}
.grid-right {
  margin-top: 25px;
  width: 100%;
  height: calc(100vh - 90px);
  display: grid;
  grid-template-rows: 1fr 1fr;
  grid-gap: 1rem;
}
.right-one {
  background: inherit 0% 0% no-repeat padding-box;
  box-shadow: 0px 10px 25px #00000008;
  border: 0.5px solid #e8e8e8;
  border-radius: 10px;
  opacity: 1;
  overflow-y: auto;
}
.right-two {
  background: inherit 0% 0% no-repeat padding-box;
  box-shadow: 0px 10px 25px #00000008;
  border: 0.5px solid #e8e8e8;
  border-radius: 10px;
  opacity: 1;
  overflow-y: auto;
}
.ini-space {
  padding: 12px 10px 10px;
}
.right-one .img-right {
  height: 30px;
}
.danger {
  color: #e6496a;
}
.success {
  color: #1abcb0;
}
</style>
