<template>
    <main class="flex flex-col gap-8">
        <Header/>
        <div class="max-w-2xl mx-auto pt-24 px-8">
            <div>
                <h1 class="text-4xl md:text-6xl font-semibold">{{ title ?? "記事が見つかりません" }}</h1>
                <p class="mt-2" v-if="!!author">by: {{ author }}</p>
            </div>
            <ContentDoc
                id="document"
                class="mt-4">
                <template #not-found>
                    <p>すみません、記事が見つかりませんでした、、、</p>
                    <NuxtLink to="/">ホームへ戻る</NuxtLink>
                </template>
            </ContentDoc>
        </div>
        <Footer/>
    </main>
</template>
<script setup lang="ts">
const route = useRoute()

const { data } = await useAsyncData('page-data', () => queryContent(`/blog/${route.params.blog}`).findOne())
const { title, author } = data.value ?? {} as { [key: string]: string }
</script>
<style>
#document > h1 {
    font-size: 40px;
    font-weight: bold;
}
#document > h2 {
    font-size: 24px;
    font-weight: bold;
    margin-top: 32px;
}
#document > blockquote {
    padding: 8px 12px;
    margin: 8px 0;
    background-color: #f1f5f9;
    border-left: solid 2px #cbd5e1;
    border-radius: 4px;
}
#document ul,
#document ol {
    margin: 8px 0;
    padding-left: 1.25rem; /* ルートのインデント */
    list-style-position: outside;
}

#document ul {
    list-style-type: disc;
}

#document ol {
    list-style-type: decimal;
}

#document li {
    margin: 4px 0;
}

/* ネストされたリストはさらに内側へ */
#document ul ul,
#document ol ol,
#document ul ol,
#document ol ul {
    margin-top: 4px;
    padding-left: 1rem;
}
#document > * > img {
    margin: 16px 0;
    border-radius: 8px;
    max-height: 500px;
}
</style>