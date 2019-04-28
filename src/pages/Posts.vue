
<template>
  <Layout>
    <ul>
      <li v-for="{ node } in $page.allPost.edges" :key="node._id">
        <router-link :to="node.path">
          <h2>{{ node.title }}</h2>
        </router-link>
        <span>{{ node.date }}</span>
        <div v-html="node.desc" />
      </li>
    </ul>
  </Layout>
</template>

<page-query>
  query Posts ($page: Int) {
    allPost (page: $page) {
      edges {
        node {
          _id
          title
          date (format: "D MMMM, YYYY")
          path
        }
      }
    }
  }
</page-query>

<style scoped>
  ul {
    list-style-type: none;
    padding: 0;
  }
  ul li {
    margin-bottom: 20px;
  }
  ul li a h2 {
    margin-bottom: 10px;
  }
  span {
    font-size: 80%;
    padding: 0;
  }
  ul li p:first-child {
    margin-top: 3px;
  }
  ul li p {
    margin: 0;
    line-height: 1.5;
  }
</style>
