<template>
  <div class="singlePersonContainer" data-index="indexInArray">
    <div class="containerWithoutButton">
      <img :src="singlePersonProfile.picture" />
      <p
        class="name-Paragraph"
        v-text="
          singlePersonProfile.name.title +
          ' ' +
          singlePersonProfile.name.first +
          ' ' +
          singlePersonProfile.name.last
        "
      ></p>
      <p class="title-paragraph" v-text="singlePersonProfile.title"></p>
      <p
        class="connectionsParagraph"
        v-text="singlePersonProfile.mutualConnections + ' mutual connections'"
      ></p>
    </div>
    <button
      type="button"
      class="connectButton"
      @click="changePendingState($event)"
    >
      Connect
    </button>
    <button type="button" class="closeButton" @click="removeProfile($event)">
      X
    </button>
  </div>
</template>

<script>
export default {
  name: "SinglePersonCard",
  props: {
    singlePersonProfile: Object,
    indexInArray: Number,
  },
  methods: {
    changePendingState(event) {
      if (event.target.innerText === "Connect") {
        this.$emit("newPendingState", "increase");
        event.target.innerText = "Pending";
      } else {
        this.$emit("newPendingState", "decrease");
        event.target.innerText = "Connect";
      }
    },
    removeProfile(event) {
      const buttonSibling =
        event.target.parentElement.querySelector(".connectButton");
      const dataForRemovel = [buttonSibling.innerText, this.indexInArray];
      this.$emit("removeIt", dataForRemovel);
    },
  },
};
</script>

<style scoped>
.singlePersonContainer {
  margin: 1%;
  border: 0.25vmin solid black;
  border-radius: 1.5vmin;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  position: relative;
}

img {
  width: 15vmin;
  height: 15vmin;
  border-radius: 50%;
  margin-top: 5%;
}

.name-Paragraph {
  margin-top: 5%;
  margin-bottom: 2.5%;
  font-weight: 600;
}

.title-paragraph {
  margin-block: 0;
  font-size: 1rem;
  color: rgb(128, 128, 128);
}

.connectionsParagraph {
  /* margin: 0; */
  font-size: 0.9rem;
}

.connectButton {
  font-size: 1.25rem;
  background-color: transparent;
  color: blue;
  padding-inline: 3vmin;
  padding-block: 0.75vmin;
  border-color: blue;
  border-radius: 2.5vmin;
  margin-bottom: 5%;
}

.closeButton {
  border-radius: 50%;
  position: absolute;
  top: 2%;
  right: 3%;
}
</style>
