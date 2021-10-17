<template>
  <div class="contents-wrapper">
    <!-- サイドナビ -->
    <aside class="side-nav">
      <div>
        <nav>
          <a>
            <img
              :src="`${path}logo.png`"
              class="nav-logo"
              width="85"
              height="85"
            />
          </a>
          <a
            class="nav-item"
            v-for="item in navList"
            :key="`nav-${item.titleEg}`"
          >
            <div class="nav-title-eg">{{ item.titleEg }}</div>
            <div class="nav-title-jp">{{ item.titleJp }}</div>
          </a>
        </nav>
        <div class="nav-copyright">© 2021 nezuminomori Co.,Ltd.</div>
      </div>
    </aside>
    <!-- メインコンテンツ -->
    <main class="contents">
      <div class="contents-title-wrapper">
        <h1 class="contents-title">Welcome to<br />my Portfolio!</h1>
      </div>
      <!-- profile -->
      <section class="profile">
        <div class="profile-title">
          <h2 class="profile-title-eg">Profile</h2>
          <span class="profile-title-jp">自己紹介</span>
        </div>
        <div class="profile-wrapper">
          <img
            :src="`${path}profile_logo.jpg`"
            class="profile-logo"
            width="150"
            height="150"
          />
          <div class="profile-contnts">
            <dl>
              <dt>出身</dt>
              <dd>北海道</dd>
              <dt>趣味</dt>
              <dd>
                猫、齧歯類、爬虫類が好き。
                <br />
                ディズニーリゾート、キャラクター、映画、楽曲とにかくディズニーが大好きです！
              </dd>
              <dt>経歴</dt>
              <dd>
                <table>
                  <tbody>
                    <tr>
                      <th>2016年3月</th>
                      <td>情報系専門学校を卒業、SES企業に入社</td>
                    </tr>
                    <tr>
                      <th>2018年9月</th>
                      <td>映像制作企業の社内エンジニアとして正社員転職</td>
                    </tr>
                    <tr>
                      <th>2020年1月～</th>
                      <td>
                        家具EC販売企業でフロントエンドとして業務委託で勤務
                      </td>
                    </tr>
                  </tbody>
                </table>
              </dd>
              <dd>
                <a
                  v-for="item in profileIconList"
                  class="profile-icon"
                  :key="item.title"
                  :href="item.link"
                  target="_blank"
                >
                  <i :class="item.class" />
                </a>
              </dd>
            </dl>
          </div>
        </div>
      </section>

      <!-- skills -->
      <section class="skills">
        <div class="skills-title">
          <h2 class="skills-title-eg">Skills</h2>
          <span class="skills-title-jp">スキル一覧</span>
        </div>
        <div v-for="item in skillsList" :key="item.title">
          <h3 class="skills-skill-title">{{ item.title }}</h3>
          <div class="skills-skill-list">
            <i
              v-for="(icon, index) in item.iconList"
              :key="`${item.title}-${index}`"
              :class="icon"
              class="skills-skill-icon"
            />
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
import "devicon";

const PATH = "/image/";

export default {
  name: "App",
  components: {},
  data() {
    return {
      path: PATH,
      navList: [
        { titleEg: "profile", titleJp: "自己紹介" },
        { titleEg: "skills", titleJp: "スキル一覧" },
        { titleEg: "works", titleJp: "作ったもの" },
        { titleEg: "connect", titleJp: "連絡先" },
      ],
      profileIconList: [
        {
          title: "Twitter",
          class: "ph-twitter-logo-fill",
          link: "https://twitter.com/nezumi_no_mori",
        },
        {
          title: "GitHub",
          class: "ph-github-logo-fill",
          link: "https://github.com/nezuminomori",
        },
        {
          title: "Qiita",
          class: "ph-notebook-fill",
          link: "https://qiita.com/nezumori",
        },
      ],
      skillsList: [
        {
          title: "frontend...",
          iconList: [
            "devicon-html5-plain",
            "devicon-css3-plain",
            "devicon-sass-original",
            "devicon-jquery-plain",
            "devicon-bootstrap-plain",
            "devicon-vuejs-plain",
          ],
        },
        { title: "backend...", iconList: ["devicon-php-plain"] },
        {
          title: "tool...",
          iconList: [
            "devicon-github-original",
            "devicon-sourcetree-original",
            "devicon-vscode-plain",
            "devicon-slack-plain",
            "devicon-xd-plain",
            "devicon-jira-plain",
          ],
        },
        {
          title: "Studying!",
          iconList: [
            "devicon-vscode-plain",
            "devicon-firebase-plain",
            "devicon-laravel-plain",
          ],
        },
      ],
    };
  },
};
</script>

<style scoped lang="scss">
@import "./assets/scss/destyle.scss";
@import url("https://fonts.googleapis.com/css2?family=Quicksand:wght@400;700&display=swap");

$color-accent-button: #5eaaa8;
$color-accent-bg: #a3d2ca;
$color-base: #f7f3e9;
$color-border: #505050;
$color-text: #505050;
$color-text-hover: #999999;

$font-eg: "Quicksand", sans-serif;

@mixin section-title() {
  border-bottom: solid 1px $color-border;
  margin-bottom: 20px;
}

@mixin section-title-eg() {
  display: inline-block;
  font-family: $font-eg;
  font-size: 2.4rem;
  margin-right: 10px;
}

@mixin section-title-jp() {
  display: inline-block;
  font-size: 1.4rem;
}

.contents-wrapper {
  display: flex;
  color: $color-text;
  font-size: 1.2rem;
}

.side-nav {
  position: sticky;
  top: 0;
  background-color: $color-accent-bg;
  width: 200px;
  height: 100vh;
  text-align: center;

  .nav-logo {
    margin: 40px auto 50px;
    border-radius: 5%;
  }

  .nav-item {
    margin-bottom: 30px;
    display: block;
    cursor: pointer;
  }

  .nav-title-eg {
    font-family: $font-eg;
    font-size: 2.4rem;
    text-transform: capitalize;
  }

  .nav-title-jp {
    font-family: $font-eg;
    font-size: 1.4rem;
  }

  .nav-copyright {
    width: 200px;
    position: absolute;
    bottom: 15px;
  }
}

.contents {
  padding: 4%;
  background-color: $color-base;
  width: calc(100% - 200px);

  .contents-title-wrapper {
    text-align: center;
    padding: 60px 0 120px;
  }

  .contents-title {
    display: inline-block;
    text-align: left;
    font-family: Impact;
    font-size: 12rem;
    line-height: 10rem;
    white-space: nowrap;
    background-image: url("/image/mv_bg.jpg");
    background-position: center;
    background-size: cover;
    background-clip: text;
    -webkit-text-fill-color: #ffffff2b;
  }
}

.profile {
  margin-bottom: 80px;

  .profile-title {
    @include section-title;
  }

  .profile-title-eg {
    @include section-title-eg;
  }

  .profile-title-jp {
    @include section-title-jp;
  }

  .profile-wrapper {
    display: flex;
  }

  .profile-logo {
    margin-right: 30px;
  }

  .profile-contnts {
    dt {
      font-size: 1.4rem;
    }

    dd {
      margin-bottom: 15px;
    }

    th {
      padding-right: 5px;
    }

    .profile-icon {
      font-size: 2.6rem;
      margin-right: 5px;

      &:hover {
        color: $color-text-hover;
      }
    }
  }
}

.skills {
  margin-bottom: 80px;

  .skills-title {
    @include section-title;
  }

  .skills-title-eg {
    @include section-title-eg;
  }

  .skills-title-jp {
    @include section-title-jp;
  }

  .skills-skill-title {
    font-family: $font-eg;
    font-size: 1.6rem;
    font-weight: bold;
    margin-bottom: 10px;
  }

  .skills-skill-list {
    margin-bottom: 20px;
  }

  .skills-skill-icon {
    font-size: 4rem;
    margin-right: 15px;
  }
}
</style>
