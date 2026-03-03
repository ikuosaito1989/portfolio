<script setup lang="ts">
const navItems = [
  { label: "ABOUT", href: "#about" },
  { label: "PORTFOLIO", href: "#portfolio" },
  { label: "SKILLS", href: "#skills" },
  { label: "CAREER", href: "#career" },
  { label: "CONTACT", href: "#contact" }
]

const portfolioItems = [
  {
    id: 1,
    title: "olcar（オルカー）",
    status: "作業中",
    description: "個人開発のアイデア検証サービス。"
  },
  {
    id: 2,
    title: "みんなの洋楽ランキング",
    status: "サービス終了",
    description: "洋楽のランキング共有サイト。"
  },
  {
    id: 3,
    title: "プロフィールサイト",
    status: "制作完了",
    description: "自分自身を紹介するためのサイト。"
  },
  {
    id: 4,
    title: "ITunEsTooL",
    status: "作業中",
    description: "音楽データ整理のためのツール。"
  },
  {
    id: 5,
    title: "Feed bank",
    status: "サービス終了",
    description: "RSSフィードを収集・整理するサービス。"
  },
  {
    id: 6,
    title: "検証用bot",
    status: "譲渡済",
    description: "検証用のbot開発プロジェクト。"
  }
]

const skillItems = [
  { name: "HTML / CSS", rating: 4 },
  { name: "Javascript", rating: 4 },
  { name: "Vue.js", rating: 3 },
  { name: "Nuxt.js", rating: 3 },
  { name: "Figma", rating: 4 }
]

const careerItems = [
  {
    term: "2023.3 - 現在",
    org: "株式会社クリエイティブリソースインスティチュート",
    role: "フロントエンドエンジニア",
    summary: [
      "LPの制作",
      "既存サイトの改修など"
    ]
  },
  {
    term: "2021.3 - 2023.2",
    org: "株式会社ABCフロンティア",
    role: "フロントエンドエンジニア",
    summary: [
      "サイト制作",
      "サービスの保守",
      "google analyticsを使用したアクセス分析"
    ]
  },
  {
    term: "2020.4 - 2021.2",
    org: "株式会社AAA",
    role: "フロントエンドエンジニア",
    summary: [
      "LPの制作"
    ]
  }
]
</script>

<template>
  <div class="page">
    <header class="hero" id="top">
      <nav class="nav">
        <div class="logo">portfolio</div>
        <div class="nav-links">
          <a v-for="item in navItems" :key="item.href" :href="item.href">
            {{ item.label }}
          </a>
        </div>
      </nav>

      <div class="hero-grid">
        <div class="hero-media">
          <div class="hero-image">
            <div class="hero-ring"></div>
            <div class="hero-avatar">IS</div>
          </div>
        </div>
        <div class="hero-copy">
          <p class="eyebrow">Profile</p>
          <h1 class="name">伊藤 翔太郎</h1>
          <p class="role">フロントエンドエンジニア</p>
          <p class="intro">
            Webサイトの構築やUIデザインが得意なフロントエンドエンジニア。自分らしさと
            使いやすさを両立させることを意識して制作しています。
          </p>
          <div class="hero-cta">
            <a class="button" href="#contact">Contact me</a>
            <a class="ghost" href="#portfolio">View portfolio</a>
          </div>
        </div>
      </div>
    </header>

    <main class="content">
      <section id="about" class="section about">
        <div class="section-head">
          <h2>ABOUT</h2>
          <p>東京で活動するフロントエンドエンジニアです。</p>
        </div>
        <div class="card about-card">
          <p>
            Webサイトの構築やUIデザインが得意なフロントエンドエンジニア。自分らしさと
            使いやすさを両立させることを意識して制作しています。
          </p>
        </div>
      </section>

      <section id="portfolio" class="section">
        <div class="section-head">
          <h2>PORTFOLIO</h2>
          <p>主に個人開発で制作したサービス・ツールの一覧です。</p>
        </div>
        <div class="portfolio-grid">
          <NuxtLink
            v-for="item in portfolioItems"
            :key="item.id"
            class="portfolio-card"
            :to="`/portfolio/${item.id}`"
          >
            <div class="portfolio-title">{{ item.title }}</div>
            <div class="portfolio-status">{{ item.status }}</div>
            <p class="portfolio-desc">{{ item.description }}</p>
          </NuxtLink>
        </div>
      </section>

      <section class="section link-section">
        <div class="link-card">
          <p>このサイトの概要は</p>
          <NuxtLink class="link" to="/portfolio/2">こちら</NuxtLink>
        </div>
      </section>

      <section id="skills" class="section">
        <div class="section-head">
          <h2>SKILLS</h2>
          <p>使用経験のあるスキルの自己評価です。</p>
        </div>
        <div class="skills-grid">
          <div v-for="skill in skillItems" :key="skill.name" class="skill-card">
            <div class="skill-name">{{ skill.name }}</div>
            <div class="stars" :style="{ '--rating': skill.rating }">
              <span class="stars-back">★★★★★</span>
              <span class="stars-front">★★★★★</span>
            </div>
          </div>
        </div>
      </section>

      <section id="career" class="section">
        <div class="section-head">
          <h2>CAREER</h2>
          <p>これまでの経歴</p>
        </div>
        <div class="career-list">
          <div v-for="career in careerItems" :key="career.term" class="career-item">
            <div class="career-term">{{ career.term }}</div>
            <div class="career-info">
              <h3>{{ career.org }}</h3>
              <p class="career-role">{{ career.role }}</p>
              <ul>
                <li v-for="line in career.summary" :key="line">{{ line }}</li>
              </ul>
            </div>
          </div>
        </div>
      </section>

      <section class="section">
        <div class="section-head">
          <h2>ソーシャル</h2>
          <p>活動先・SNS</p>
        </div>
        <div class="social-grid">
          <a class="social-item" href="#">Twitter</a>
          <a class="social-item" href="#">GitHub</a>
          <a class="social-item" href="#">Qiita</a>
        </div>
      </section>

      <section id="contact" class="section contact">
        <div class="section-head">
          <h2>CONTACT</h2>
          <p>ご相談・お問い合わせはこちらから</p>
        </div>
        <form class="contact-form">
          <label>
            <span>お名前</span>
            <input type="text" name="name" placeholder="お名前" />
          </label>
          <label>
            <span>メールアドレス</span>
            <input type="email" name="email" placeholder="example@email.com" />
          </label>
          <label>
            <span>内容</span>
            <textarea name="message" rows="5" placeholder="お問い合わせ内容"></textarea>
          </label>
          <button type="button">送信する</button>
        </form>
      </section>

      <section class="section">
        <div class="section-head">
          <h2>Storybook</h2>
          <p>UI一覧はこちらから</p>
        </div>
        <a
          class="storybook-link"
          href="https://quirky-hoover-d5f9da.netlify.com"
          target="_blank"
          rel="noopener noreferrer"
        >
          Storybookを見る
        </a>
      </section>
    </main>

    <footer class="footer">
      <p>© 2024 ik-saito.net</p>
      <a href="#top">Back to top</a>
    </footer>
  </div>
</template>
