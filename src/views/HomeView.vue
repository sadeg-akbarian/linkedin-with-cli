<template>
  <div class="homeView-container">
    <header>
      <p>No pending invitations</p>
      <button type="button">Manage</button>
    </header>
    <main>
      <div class="areaContainer">
        <p class="areaContainer-text">People you may know in Aachen Area</p>
        <button type="button" class="areaContainer-button">See all</button>
      </div>
      <div class="profileArea">
        <SinglePersonCard
          v-for="profile of this.profileList"
          :key="profile.id"
          :singlePersonProfile="profile"
        />
      </div>
    </main>
  </div>
</template>

<script>
import SinglePersonCard from "@/components/SinglePersonCard.vue";

export default {
  data() {
    return {
      urlOfBackend:
        "https://dummy-apis.netlify.app/api/contact-suggestions?count=1",
      profileList: [],
    };
  },
  name: "HomeView",
  components: {
    SinglePersonCard,
  },
  methods: {
    initalDataFromBackend() {
      for (let i = 0; i < 8; i++) {
        fetch(this.urlOfBackend)
          .then((response) => {
            if (response.ok === true) {
              return response.json();
            } else {
              alert("Error: Profiles could not be loaded!!!");
            }
          })
          .then((data) => {
            data[0].id =
              Date.now().toString(36) + Math.random().toString(36).substr(2);
            this.profileList.push(data[0]);
          });
      }
    },
  },
  created() {
    this.initalDataFromBackend();
  },
};
</script>

<style scoped>
header,
main {
  background-color: white;
  width: 70vw;
  font-size: 20px;
  border-radius: 2vmin;
}

header {
  display: flex;
  justify-content: space-between;
  padding-inline: 3%;
}

header > p {
  font-weight: 600;
}

header > button {
  all: unset;
}

header > * {
  margin-block: 2%;
}

main {
  height: 85vh;
  margin-top: 2vh;
}

.areaContainer {
  display: flex;
  justify-content: space-between;
  height: 10%;
}

.areaContainer-text {
  margin-left: 2rem;
}

.areaContainer-button {
  all: unset;
  margin-right: 2rem;
}

.areaContainer-button:hover {
  color: red;
}

.areaContainer-button:active {
  font-weight: 800;
}

.profileArea {
  width: 100%;
  height: 90%;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  padding-inline: 0.5%;
}
</style>
