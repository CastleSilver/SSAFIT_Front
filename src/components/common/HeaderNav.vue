<template>
  <v-app>
    <div>
      <v-app-bar app flat style="height: 100px; background-color: #da0037">
        <div class="headerbar">
          <a href="/" class="ssafit" style="font-family: KickerTrialBlack">
            SSAFIT &nbsp;</a
          >
          <v-btn to="/user/login" color="black" class="login"> Log In </v-btn>
        </div>
        <div>
          <button @click="hamburgerMenu" class="hamburgerBtn">
            <font-awesome-icon icon="fa-solid fa-bars" class="hamburger" />
          </button>
        </div>
      </v-app-bar>
      <!--비디오 영상 출력 -->
      <div
        class="tm-hero d-flex justify-content-center align-items-center"
        id="tm-video-container"
        style="margin-top: 100px; background-color: #da0037"
      >
        <i id="tm-video-control-button" class="fas fa-pause"></i>
        <video autoplay muted loop id="tm-video" height="300px">
          <source :src="require('@/assets/video/video.mp4')" type="video/mp4" />
        </video>
        <video autoplay muted loop id="tm-video" height="300px">
          <source
            :src="require('@/assets/video/video1.mp4')"
            type="video/mp4"
          />
        </video>
        <video autoplay muted loop id="tm-video" height="300px">
          <source
            :src="require('@/assets/video/video2.mp4')"
            type="video/mp4"
          />
        </video>
        <i id="tm-video-control-button" class="fas fa-pause"></i>
      </div>

      <v-main class="main" style="background-color: #da0037">
        <v-row class="main-divider">
          <div :class="[{ leftMenu: true }, { hide: isClosed }]">
            <v-sheet rounded="lg" class="leftBar">
              <v-list color="transparent">
                <v-list-item
                  v-for="(link, idx) in links"
                  :key="idx + 'I'"
                  :to="{ path: link.router }"
                  class="router"
                  link
                >
                  <v-list-item-icon>
                    <img :src="`${link.icon}`" style="width: 40px" />
                  </v-list-item-icon>
                  <v-list-item-content>
                    {{ link.title }}
                  </v-list-item-content>
                </v-list-item>

                <v-divider class="my-2"></v-divider>
                <v-list-item
                  v-for="(link, idx) in links2"
                  :key="idx + 'R'"
                  :to="{ path: link.router }"
                  class="router"
                  link
                >
                  <v-list-item-icon>
                    <img :src="`${link.icon}`" style="width: 40px" />
                  </v-list-item-icon>
                  <v-list-item-content>
                    {{ link.title }}
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-sheet>
          </div>
          <div :class="[{ rightMain: true }, { paddingRightMain: !isClosed }]">
            <v-sheet min-height="100vh" rounded="lg">
              <router-view />
            </v-sheet>
          </div>
        </v-row>
      </v-main>
    </div>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    isClosed: true,
    links: [
      {
        title: "홈",
        router: "/",
        icon: "https://img.icons8.com/stickers/100/000000/home-page.png",
      },
      {
        title: "검색",
        router: "/search",
        icon: "https://img.icons8.com/stickers/100/000000/search.png",
      },
    ],
    links2: [
      {
        title: "찜리스트",
        router: "/vlist/like",
        icon: "https://img.icons8.com/stickers/100/000000/like.png",
      },
      {
        title: "시청기록",
        router: "/vlist/watched",
        icon: "https://img.icons8.com/stickers/100/000000/laptop-play-video.png",
      },
    ],
  }),
  methods: {
    hamburgerMenu() {
      this.isClosed = !this.isClosed;
    },
  },
};
</script>
<style scoped>
/* 홈, 검색, 찜리스트, 시청기록 나타내는 왼쪽 메뉴바 */
.leftMenu {
  position: fixed;
  width: 200px;
}
/* 컨텐츠 표시 오른쪽 메인 공간 */
.rightMain {
  margin-left: 200px;
  width: 100%;
}
.leftBar {
  width: 180px;
}

.headerbar {
  height: 80px;
  display: flex;
  justify-content: space-between;
}

.main {
  background-color: grey;
}
.main-divider {
  margin: 0px 20px;
}
.ssafit {
  text-decoration: none;
  color: black;
  margin: 20px 20px;
  font-weight: bolder;
  font-size: 60px;
}
.router {
  color: black;
  text-decoration: none;
}
.login {
  text-decoration: none;
  margin-top: 40px;
  margin-right: 30px;
  color: white;
  font-size: 20px;
}
.v-sheet.rounded-lg {
  background-color: #ededed;
}
/* 햄버거 버튼 숨겨 */
.hamburger {
  display: none;
}
@media screen and (max-width: 768px) {
  .main {
    background-color: rgb(84, 84, 84);
  }
  /* 위는 삭제 */
  .main * {
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font: inherit;
    display: block;
    width: auto;
    height: auto;
  }
  .leftMenu {
    visibility: visible;
    opacity: 1;
    position: fixed;
    z-index: 2;
    margin: 0px;
    width: 100%;
    height: 200px;
    transition: all 0.3s;
  }
  .leftBar {
    border-radius: 0px !important;
    width: 100%;
  }
  .main-divider {
    flex-direction: column;
  }
  /* 상단 이미지 & 인사문구 가리기 */
  .run {
    display: none;
  }
  .message {
    display: none;
  }
  /* 햄버거 버튼 나오고 회원 버튼 사라짐 */
  .userMenu {
    display: none;
  }
  .hamburger {
    display: block;
    font-size: 25px;
  }
  .hide {
    visibility: hidden;
    opacity: 0;
    height: 0px;
  }
  .paddingRightMain {
    padding-top: 200px;
    transition: all 0.2s;
  }
  .rounded-lg {
    border-radius: 0 !important;
  }
  .v-application .rounded-lg {
    border-radius: 0px !important;
  }
  .v-list > a * {
    display: inline-block;
    vertical-align: middle;
  }
  .v-list > a {
    text-align: center;
  }
  .hamburgerBtn {
    margin: 0px 15px;
  }
}
</style>
