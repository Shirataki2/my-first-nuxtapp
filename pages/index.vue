<template>
  <div>
    <table>
      <caption>好きなものリスト</caption>
      <thead>
        <tr>
          <th>ID</th>
          <th>名前</th>
          <th>好きなもの</th>
        </tr>
      </thead>
      <tbody v-for="user in users" :key="user.id">
        <tr>
          <td>{{ user.id }}</td>
          <td>{{ user.name }}</td>
          <td>
            <ul>
              <li v-for="(item, i) in user.like" :key="i">{{ item }}</li>
            </ul>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async asyncData() {
    const { data } = await axios.get("https://api.myjson.com/bins/yzzof");
    return {
      users: data
    };
  }
};
</script>

<style scoped>
table {
  width: 100%;
}

tbody:nth-child(odd) {
  background: #eee;
}

ul {
  padding: 0;
  margin: 5px 0;
}

li {
  display: inline;
  margin: 0 5px;
  padding: 5px;
  background-color: #ccc;
  border-radius: 20px;
}
</style>