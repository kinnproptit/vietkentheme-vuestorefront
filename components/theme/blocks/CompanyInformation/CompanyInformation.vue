/* eslint-disable vue/html-self-closing */
<template>
  <section class="container px15">
    <div class="row center-xs">
      <div class="background" style="margin-bottom: 70px;">
        <header class="col-md-12">
          <h2 class="align-center cl-accent">{{ $t('Bleib gesund mit Selbstheilung') }}</h2>
          <h4
            class="align-center"
          >{{ $t('Wie wir die revolutionärsten Lebensmittel unserer Zeit entwickeln?')}}</h4>
        </header>
        <!-- <div class="split">
          <div class="side">
            <ul class="fa-ul">
              <li v-for="item in data1" :key="item.id">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  xmlns:xlink="http://www.w3.org/1999/xlink"
                  version="1.1"
                  id="Capa_1"
                  x="0px"
                  y="0px"
                  viewBox="0 0 367.805 367.805"
                  style="enable-background:new 0 0 367.805 367.805;"
                  xml:space="preserve"
                  width="23px"
                  heigth="23px"
                >
                  <g>
                    <path
                      style="fill:#3BB54A;"
                      d="M183.903,0.001c101.566,0,183.902,82.336,183.902,183.902s-82.336,183.902-183.902,183.902   S0.001,285.469,0.001,183.903l0,0C-0.288,82.625,81.579,0.29,182.856,0.001C183.205,0,183.554,0,183.903,0.001z"
                    />
                    <polygon
                      style="fill:#D4E1F4;"
                      points="285.78,133.225 155.168,263.837 82.025,191.217 111.805,161.96 155.168,204.801    256.001,103.968  "
                    />
                  </g>
                </svg>
                <span>{{ item.content }}</span>
              </li>
            </ul>
          </div>
          <div class="side">
            <ul class="fa-ul">
              <li v-for="item in data2" :key="item.id">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  xmlns:xlink="http://www.w3.org/1999/xlink"
                  version="1.1"
                  id="Capa_1"
                  x="0px"
                  y="0px"
                  viewBox="0 0 367.805 367.805"
                  style="enable-background:new 0 0 367.805 367.805;"
                  xml:space="preserve"
                  width="23px"
                  heigth="23px"
                >
                  <g>
                    <path
                      style="fill:#3BB54A;"
                      d="M183.903,0.001c101.566,0,183.902,82.336,183.902,183.902s-82.336,183.902-183.902,183.902   S0.001,285.469,0.001,183.903l0,0C-0.288,82.625,81.579,0.29,182.856,0.001C183.205,0,183.554,0,183.903,0.001z"
                    />
                    <polygon
                      style="fill:#D4E1F4;"
                      points="285.78,133.225 155.168,263.837 82.025,191.217 111.805,161.96 155.168,204.801    256.001,103.968  "
                    />
                  </g>
                </svg>
                <span>{{ item.content }}</span>
              </li>
            </ul>
          </div>
        </div>-->
        <div class="center-xs">
          <div class="usp-slider">
            <a
              href="#"
              class="usp-icon"
              v-for="icon in icons"
              :class="{active: icon.active}"
              :key="icon.id"
              @click="activateIcon(icon.id)"
            >
              <img :src="icon.icon" />
            </a>
            <!-- <span class="arrow" /> -->
            <div class="usp-bubbles">
              <div class="inner-wrapper">
                <span class="usp-bubble" v-for="item in data" :key="item.id">
                  <div v-if="item.active">
                    <strong>{{ item.title }}:</strong>
                    {{ item.content }}
                  </div>
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'CompanyInformation',
  data() {
    return {
      data: [
        {
          id: 0,
          title: 'Naturbelassen',
          active: true,
          content:
            'Wirkstoffe aus natürlicher, pflanzlicher Quelle und in bioaktivster Form.'
        },
        {
          id: 1,
          title: 'Premium Qualität',
          active: false,
          content:
            'Aus den weltweit besten Anbaugebieten und von den führenden Herstellern.'
        },
        {
          id: 2,
          title: 'Pure-Reinheit',
          active: false,
          content:
            'Pure Wirkstoffe ohne chemische Zusätze. Frei von Belastungen und Gentechnik.'
        },
        {
          id: 3,
          title: 'Innovation',
          active: false,
          content:
            'Kooperation und Erfahrungstausch mit Apotheken, Kliniken, Ärzten, Heilpraktikern und ganzheitlichen Therapeuten sowie führenden Wissenschaftlern und Qualitäts-Herstellern zur Entwicklung einzigartiger, optimierter Rezepturen und Produkte für Sie.'
        },
        {
          id: 4,
          title: 'Nachhaltigkeit',
          active: false,
          content:
            'Nachhaltig angebaute Rohstoffe. Umweltfreundliche Verpackungen aus Glas oder kompostierbarer Stärke.'
        },
        {
          id: 5,
          title: 'Transparenz',
          active: false,
          content:
            'Täglich geöffneter Store - in Köln Innenstadt. Volldeklaration aller Inhaltsstoffe und Verfahren.'
        }
      ],
      icons: [
        {
          id: 0,
          active: true,
          icon: '../assets/star.svg'
        },
        {
          id: 1,
          active: false,
          icon: '../assets/grow.svg'
        },
        {
          id: 2,
          active: false,
          icon: '../assets/light.svg'
        },
        {
          id: 3,
          active: false,
          icon: '../assets/like.svg'
        },
        {
          id: 4,
          active: false,
          icon: '../assets/smile.svg'
        },
        {
          id: 5,
          active: false,
          icon: '../assets/design.svg'
        }
      ]
    };
  },
  methods: {
    activateIcon: function(index) {
      console.log(index);
      this.data = this.data.map(({ id, title, active, content }) => ({
        id,
        title,
        active: false,
        content
      }));
      this.data[index].active = true;

      this.icons = this.icons.map(({ id, active, icon }) => ({
        id,
        active: false,
        icon
      }));
      this.icons[index].active = true;
    }
  }
};
</script>

<style lang="scss" scoped>
.background {
  width: 70%;
  background: #ffffff;
  background: rgba(255, 255, 255, 0.8);
}

.split {
  display: flex;
}
.side {
  width: 50%;
}

.fa-ul {
  list-style: none;
  padding: 0.75rem;
  margin: 0;
}

li {
  display: flex;
  align-items: center;
  margin: 1.5rem 0;
}

li span {
  margin-left: 0.5rem;
}
@media (min-width: 900px) {
  .background {
    margin-top: -20%;
  }
}

.usp-slider {
  position: relative;
  text-align: center;
  margin-left: 5px;
  margin-right: 5px;
  height: 50px;
  margin-bottom: 105px;
}
@media screen and (min-width: 600px) {
  .usp-slider {
    height: 75px;
    margin-bottom: 85px;
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
  }
}

// .usp-slider a {
//   width: 20%;
//   float: left;
// }

.usp-slider a.active img {
  background-color: #e2e2e2;
}
.usp-slider a:hover img,
.usp-slider a.acttive img {
  fill: #3c3c3e;
}

.usp-slider a img {
  fill: #a3a3a3;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  margin-left: auto;
  margin-right: auto;
  padding: 10px;
}

.usp-slider a img {
  width: 24px;
  height: 24px;
}

@media screen and (min-width: 600px) {
  .usp-slider a img {
    width: 60px;
    height: 60px;
    margin: 5px;
  }
}

.usp-slider .arrow {
  position: absolute;
  bottom: -35px;
  // top: 110px;
  left: 0;
  transition: 0.3s all;
  z-index: 2;
  width: 20%;
  text-align: center;
}

.usp-slider .arrow:before {
  content: '';
  position: absolute;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 0 12px 10px 12px;
  border-color: transparent transparent #e2e2e2 transparent;
  transition-property: left;
  transition-duration: 0.6s;
  transform: translateY(-100%) translateX(-50%);
}

.usp-slider .usp-bubbles {
  position: absolute;
  top: 100%;
  left: 5px;
  right: 5px;
  background-color: #e2e2e2;
  border-radius: 20px;
  margin-top: 35px;
  font-size: 16px;
  line-height: 22px;
  -webkit-transition: all 0.4s;
  -moz-transition: all 0.4s;
  -ms-transition: all 0.4s;
  -o-transition: all 0.4s;
  transition: all 0.4s;
}

@media screen and (min-width: 600px) {
  .usp-slider .usp-bubbles {
    left: -100px;
    right: -100px;
  }
}

.usp-slider .usp-bubbles .inner-wrapper {
  display: inline-block;
  max-width: 100%;
  padding: 20px 40px;
}
</style>
