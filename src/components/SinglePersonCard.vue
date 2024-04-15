<template>
  <div class="singlePersonContainer">
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
    <button type="button" class="connectButton">Connect</button>
  </div>
</template>

<!-- 
name:Object
  first:"Kors"
  last:"Van Eldijk"
  title:"Mr"
title:"Art Director"
picture:"https://randomuser.me/api/portraits/men/79.jpg"
mutualConnections:7
backgroundImage:"https://source.unsplash.com/random/300×300"
id:"lv1529zx317ab1f0w5"
 -->

<script>
export default {
  name: "SinglePersonCard",
  props: {
    singlePersonProfile: Object,
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
</style>
