<template>
  <li>
    <img :src="imgPath" />
    <div class="wrap p5">
      <p v-if="title" class="title">
        {{ title }}
      </p>
      <p v-if="des" class="des">
        {{ des }}
      </p>
      <div
        v-if="rating !== undefined"
        class="rating"
        :style="`background-size: ${15 * rating}px 100%`"
      ></div>
      <span class="author">{{ author }}</span>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    imgName: { type: String, required: true },
    title: { type: String },
    des: { type: String },
    author: { type: String },
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
  display: flex;
  list-style: none;
  float: left;
  margin-right: 10px;
}
img {
  max-width: 100%;
  height: auto;
}
.wrap {
  background-color: #f7f7f7;
  border: solid 1px #d8d8d8;
  width: 200px;
}
.title {
  width: 200px;
  word-break: break-word;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.des {
  width: 200px;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  word-break: break-all;
  white-space: normal;
  overflow: hidden;
  text-overflow: ellipsis;
  color: #d8d8d8;
  font-size: 12px;
}
.author {
  margin-left: 5px;
  padding-left: 5px;
  vertical-align: top;
  border-left: solid 1px #d8d8d8;
  color: #d8d8d8;
}
.p5 {
  padding: 5px;
}
.rating {
  position: relative;
  display: inline-block;
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
