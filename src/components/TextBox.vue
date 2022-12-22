<template>
  <div class="text_wrap">
    <div :class="['text_group', status]">
      <textarea
        :class="status"
        :id="id"
        :placeholder="placeholder"
        :maxlength="maxlength"
        :readonly="readonly"
        :disabled="disabled"
        :value="textValue"
        @input="changeInput"
      />
      <label :for="id">{{ remainLen }}</label>
    </div>
    <button v-if="status === 'modify'" @click="save">Save</button>
  </div>
</template>

<script>
export default {
  props: {
    placeholder: { type: String, default: "주문 요청사항을 입력해주세요" },
    maxlength: { type: Number, default: 500 },
    readonly: { type: Boolean, default: false },
    disabled: { type: Boolean, default: false },
    id: { type: [Number, String], required: true },
    initText: { type: String, default: "" },
  },

  data() {
    return {
      textValue: this.initText,
    };
  },

  computed: {
    status() {
      if (this.textValue !== this.initText) return "modify";
      return "view";
    },
    remainLen() {
      return this.maxlength - this.textValue.length;
    },
  },

  methods: {
    changeInput(e) {
      this.textValue = e.target.value;
    },
    save() {
      alert("저장되었습니다.");
    },
  },
};
</script>

<style scoped>
.text_wrap {
  display: flex;
  height: 100px;
  margin: 10px;
}
.text_wrap .text_group {
  position: relative;
  width: 100%;
  height: 100%;
  display: inline-block;
  vertical-align: top;
}
.text_wrap .text_group.modify {
  width: 90%;
}

.text_group textarea {
  height: 100%;
  width: 100%;
  padding-right: 40px;
  resize: none;
  box-sizing: border-box;
  float: left;
  outline: none;
}

.text_group textarea[disabled],
.text_group textarea[disabled]::placeholder {
  color: red;
}

.text_group textarea[readonly],
.text_group textarea[readonly]::placeholder {
  color: blue;
}
.text_group .modify {
  border-color: rgb(130, 191, 195);
}

.text_group textarea + label {
  position: absolute;
  width: 40px;
  right: 0;
  bottom: 0;
  padding: 0 5px 10px 0;
  color: rgb(228, 227, 228);
}

.text_wrap button {
  color: rgb(130, 191, 195);
  background-color: white;
  border-color: rgb(228, 227, 228);
  border-width: 0.5px;
  height: 100%;
  width: 50px;
  margin-left: 5px;
  flex-grow: 1;
}
</style>
