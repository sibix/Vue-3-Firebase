<template>
  <h1>Jobs</h1>
  <div v-for="job in jobs" :key="job.id">
    <router-link :to=" {name: 'JobDetails', params: {id: job.id }} ">
      <h2>{{ job.title }}</h2>
    </router-link>
    <div class= "products">
      ID -  {{ jobs.records[0].id }} <br>
      Status - {{ jobs.records[0].fields.Status }} <br>
      Price- {{ jobs.records[0].fields.Price }} <br>
      Product Name - {{ jobs.records[0].fields.ProductName }} <br>
      Quantity Available -  {{ jobs.records[0].fields.QuantityAvailable }} <br>
      Offer price -  {{ jobs.records[0].fields.Offer-Price }} <br>
      craeted Time - {{ jobs.records[0].createdTime }} <br>
      Length - {{ jobs.records.length }} <br>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      jobs: []
    }
  },
  mounted() {
    fetch('https://api.airtable.com/v0/appQ5A4sEU3uZstcI/PRODUCTS?api_key=keyUop6Ql5CLltnDI')
      .then(res => res.json())
      .then(data => this.jobs = data)
      .catch(err => console.log(err.message))
      //console.log(this.data);
  }
}
</script>

<style>
  .products {
    text-align: left;
  }
</style>