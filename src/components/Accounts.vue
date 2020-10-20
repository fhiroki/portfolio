<template>
  <v-col class="mb-5 section-wrapper" cols="12">
    <h2 class="headline font-weight-bold mb-3">
      Accounts
    </h2>

    <v-row justify="center">
      <table>
        <tbody>
          <tr v-for="(item, i) in accounts" :key="i">
            <th>{{ item.title }}</th>
            <td v-if="item.url">
              <a :href="item.url" target="_blank">
                {{ item.content }}
              </a>
            </td>
            <td v-else>{{ item.content }}</td>
          </tr>
        </tbody>
      </table>
    </v-row>
  </v-col>
</template>

<script>
export default {
  name: "Accounts",

  data: () => ({
    accounts: [
      {
        title: "Github",
        content: "fhioki",
        url: "https://github.com/fhiroki",
      },
      {
        title: "AtCoder",
        content: "fhioki",
        url: "https://atcoder.jp/users/fhiroki",
      },
      {
        title: "Qiita",
        content: "fhioki",
        url: "https://qiita.com/fhiroki",
      },
    ],
  }),
};
</script>

<style lang="scss" scoped>
.section-wrapper {
  th {
    font-size: 20px;
  }
  td {
    font-size: 20px;
  }
}
a {
  text-decoration: none;
}
</style>
