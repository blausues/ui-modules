<template>
  <li>
    <img :src="imgPath" />
    <div class="wrap p5">
      <p v-if="label" class="label txt">{{ label }}</p>
      <p v-if="title" class="txt">{{ title }}</p>
      <p class="txt">
        <span class="highlight">Highlight</span>
        <span class="line">Cross Out</span>
      </p>
    </div>
    <div v-if="rating !== undefined || des" class="wrap p5">
      <div
        v-if="rating !== undefined"
        class="rating"
        :style="`background-size: ${15 * rating}px 100%`"
      ></div>
      <p v-if="des" class="des txt">{{ des }}</p>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    imgName: { type: String, required: true },
    label: { type: String },
    title: { type: String },
    des: { type: String },
    rating: { type: Number },
  },
  computed: {
    imgPath() {
      return require(`../assets/${this.imgName}`);
    },
  },
};
</script>

<style scoped>
li {
  list-style: none;
  background-color: #f7f7f7;
  border: solid 1px #d8d8d8;
  border-bottom: none;
  margin-right: 10px;
  float: left;
}
img {
  max-width: 100%;
  height: auto;
}
.wrap {
  border-bottom: solid 1px #d8d8d8;
}
.p5 {
  padding: 5px;
}
.label {
  font-size: 13px;
  color: #d8d8d8;
}
.txt {
  margin: 5px 0 5px 0;
}
.highlight {
  color: red;
}
.line {
  color: #d8d8d8;
  text-decoration: line-through;
  margin-left: 5px;
}
.des {
  color: #d8d8d8;
}
.rating {
  margin-top: 5px;
  position: relative;
  height: 15px;
  width: 75px;
  background: linear-gradient(to right, gold, gold);
  background-color: #dddddd;
  background-repeat: no-repeat;
  background-position: 0px 0px;
  background-size: 0px 100%;
}
.rating:after {
  position: absolute;
  content: "";
  height: 100%;
  width: 100%;
  background: radial-gradient(15px at center, transparent 6px, #f7f7f7 5px);
  background-position: 0px 0px;
  background-size: 15px 100%;
}
</style>
