<template>
  <section>
    <h2>{{ firstHeaderText }}</h2>
    <Request
      v-for="request in getNotDelivered"
      :key="request.id"
      :request="request"
    />
    <h2>{{ secondHeaderText }}</h2>
    <Request
      v-for="request in getDelivered"
      :key="request.id"
      :request="request"
    />
  </section>
</template>

<script>
import Request from "@/components/Request.vue";

export default {
  name: "Requests",
  components: {
    Request
  },
  props: {
    requests: {
      type: Array,
      required: true
    },
    firstHeaderText: {
      type: String,
      required: true
    },
    secondHeaderText: {
      type: String,
      required: true
    }
  },
  computed: {
    getDelivered() {
      return this.requests.filter(request => request.delivered);
    },
    getNotDelivered() {
      return this.requests.filter(request => !request.delivered);
    }
  }
};
</script>
