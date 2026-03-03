<script setup lang="ts">
const items = [
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

const route = useRoute()
const itemId = Number(route.params.id)
const item = items.find((entry) => entry.id === itemId)
</script>

<template>
  <div class="page">
    <header class="simple-header">
      <NuxtLink class="back" to="/">← Back</NuxtLink>
      <div class="header-copy">
        <p class="eyebrow">Portfolio</p>
        <h1>{{ item?.title ?? "Not found" }}</h1>
      </div>
    </header>

    <main class="content">
      <section class="section">
        <div v-if="item" class="card">
          <div class="portfolio-status">{{ item.status }}</div>
          <p class="portfolio-desc">{{ item.description }}</p>
          <p class="muted">詳細は準備中です。</p>
        </div>
        <div v-else class="card">
          <p>該当するポートフォリオが見つかりませんでした。</p>
        </div>
      </section>
    </main>
  </div>
</template>
