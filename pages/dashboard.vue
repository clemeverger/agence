<template>
  <div>
    <ul v-for="house in houses" :key="house.id">
      <NuxtLink :to="`/house/${house.id}`">
        <li>{{ house.attributes.Description }}</li>
      </NuxtLink>
    </ul>
  </div>
</template>

<script>
export default {
  name: "InspirePage",
  async asyncData() {
    const res = await fetch("http://localhost:1337/api/houses").then((res) =>
      res.json()
    );
    return { houses: res.data };
  },
};
</script>
