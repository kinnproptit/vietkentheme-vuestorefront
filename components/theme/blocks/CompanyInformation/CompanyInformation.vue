<template>
  <section class="container px15">
    <!-- <div>
      <header class="col-md-12">
        <h2 class="align-center cl-accent">{{ $t('Some helpful information.') }}</h2>
      </header>
    </div>-->
    <div class="row center-xs">
      <div class="background">
        <header class="col-md-12">
          <h2 class="align-center cl-accent">{{ $t('Some helpful information.') }}</h2>
        </header>
        <div class="split">
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
      data1: [
        {
          id: 1,
          content:
            'Lorem Ipsum is simply dummy text of the printing and typesetting industry.'
        },
        {
          id: 2,
          content:
            "Lorem Ipsum has been the industry's standard dummy text ever since the 1500s"
        },
        {
          id: 3,
          content:
            "Lorem Ipsum has been the industry's standard dummy text ever since the 1500s"
        },
        {
          id: 4,
          content:
            "Lorem Ipsum has been the industry's standard dummy text ever since the 1500s"
        }
      ],
      data2: [
        {
          id: 5,
          content:
            "Lorem Ipsum has been the industry's standard dummy text ever since the 1500s"
        },
        {
          id: 6,
          content:
            "Lorem Ipsum has been the industry's standard dummy text ever since the 1500s"
        },
        {
          id: 7,
          content:
            "Lorem Ipsum has been the industry's standard dummy text ever since the 1500s"
        },
        {
          id: 8,
          content:
            "Lorem Ipsum has been the industry's standard dummy text ever since the 1500s"
        }
      ]
    }
  }
}
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
</style>
