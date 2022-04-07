<template>
  <div>
    <p>Available: {{ available }}</p>
    <p>Description: {{ description }}</p>
    <p>Surface: {{ surface }}</p>
    <p>City: {{ city }}</p>
    <p>Price: {{ price }}</p>
  </div>
</template>
<script>
export default {
  async asyncData({ params }) {
    const house = await fetch("http://localhost:1337/api/houses/" + params.id).then((res) =>
      res.json()
    );
    return {
      available: house.data.attributes.Available,
      description: house.data.attributes.Description,
      surface: house.data.attributes.Surface,
      city: house.data.attributes.City,
      price: house.data.attributes.Price + "$",
    }
  },
};
</script>