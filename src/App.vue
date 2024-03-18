<script setup lang="ts">
import NaverIcon from "@components/icons/NaverIcon.vue"
import { ref } from "vue"
import SearchBar from "@components/SearchBar.vue"
import axios from "axios"
const searchText = ref("")
const getData = ref()
const requestAPI = (searchString: string) => {
  searchText.value = searchString
  const en = encodeURIComponent(searchString)
  axios
    .post(
      `https://nx-api.place.naver.com/graphql`,
      {
        headers: {
          "Content-Type": "application/json; charset=utf-8",
          "X-Gql-Query-Names": "restaurantList,bookmarks",
          "X-Gql-Query-Variables": en,
          "X-Xss-Protection": "1; mode=block",
        },
      }

      // @typescript-eslint/no-explicit-any
      // @ts-ignore
    )
    .then((res: any) => {
      getData.value = res.data
      // eslint-disable-next-line @typescript-eslint/no-explicit-any
      // @ts-ignore
    })
    .catch((err: any) => {
      console.error(err)
    })
}
</script>

<template>
  <header class="flex items-center justify-center">
    <div class="flex items-center justify-center gap-4 text-2xl font-bold pb-8">
      <NaverIcon class="h-8" />
      네이버플레이스
    </div>
  </header>
  <main class="w-5/6 max-w-[92%] min-w-[40rem] mx-auto">
    <SearchBar @search="requestAPI" />
  </main>
</template>
