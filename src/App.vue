<template>
  <div>
    <h2>과제 1. 카드 UI</h2>
    <ul>
      <card-vertical
        imgName="bird1.jpg"
        label="Card Label"
        title="작은 이미지"
        des="asdf"
        :rating="1"
      />

      <card-vertical imgName="bird2.jpg" />

      <card-horizon
        imgName="bird2.jpg"
        title="큰 사이즈 큰 사이즈 큰 사이즈 큰 사이즈 큰 사이즈"
        des="하나둘셋넷 하나둘셋넷 하나둘셋넷 하나둘셋넷 하나둘셋넷 하나둘셋넷 하나둘셋넷 하나둘셋넷"
        author="John Doe"
        :rating="3"
      />
    </ul>

    <h2 class="clear">과제 2. 입력 폼 UI</h2>
    1. 디폴트
    <text-box id="textBox1" />

    2. 초기 값이 있는 상태
    <text-box id="textBox2" initText="안녕하세요." />

    3. disabled
    <text-box id="textBox3" :disabled="true" />

    4. readonly
    <text-box id="textBox4" initText="읽기 전용입니다." :readonly="true" />
  </div>
</template>

<script>
import CardHorizon from "./components/CardHorizon.vue";
import CardVertical from "./components/CardVertical.vue";
import TextBox from "./components/TextBox.vue";

export default {
  name: "App",
  components: {
    CardHorizon,
    CardVertical,
    TextBox,
  },
};
</script>

<style scoped>
.clear {
  clear: both;
}
</style>
