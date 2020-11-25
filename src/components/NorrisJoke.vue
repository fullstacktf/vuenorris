<template>
  <div>
    <div class="container" v-if="icon">
      <img :src="getIcon" alt="chuck img" />
      <div>
        <p>{{ text }}</p>
        <span>{{ date }}</span>
      </div>
    </div>
    <div class="container" v-else>
      <img src="https://shortpixel.com/img/spinner2.gif" alt="loading" />loading
    </div>
  </div>
</template>

<script>
const URL = "https://api.chucknorris.io/jokes/random";
export default {
  name: "NorrisJoke",
  created() {
    this.fetchApi();
  },
  methods: {
    fetchApi() {
      fetch(URL)
        .then(res => res.json())
        .then(data => {
          this.icon = data.icon_url;
          this.text = data.value;
          this.date = data.updated_at;
        });
    }
  },
  computed: {
    getIcon() {
      return this.type === "chuck"
        ? this.icon
        : "https://pbs.twimg.com/profile_images/3681800067/52aca11437c84b556072673c70480174.jpeg";
    }
  },
  props: {
    type: {
      type: String,
      default: "chuck",
      required: false,
      validator: v => {
        return ["nicolas", "chuck"].includes(v);
      }
    }
  },
  data() {
    return {
      icon: "",
      text: "",
      date: ""
    };
  }
};
</script>

<style>
.container {
  display: inline-flex;
  max-width: 500px;
  border: 1px solid #999;
  padding: 5px;
  padding-right: 20px;
  border-radius: 10px;
  font-family: "Montserrat";
  background: #eee;
}
.container > div {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
img {
  width: 60px;
  height: 60px;
  margin-right: 10px;
}
p {
  margin: 0;
}
span {
  font-family: Arial;
  font-size: 12px;
  color: purple;
}
</style>
