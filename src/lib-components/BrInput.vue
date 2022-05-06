<script lang="ts">
import { computed, defineComponent, ref } from 'vue';

export default defineComponent({
  setup() {
    const inputEl = ref(null);
    const isFocused = ref(false);

    const cls = computed(() => {
      const prefix = 'br-input';
      return {
        [`${prefix}-focused`]: isFocused.value,
      };
    })

    return {
      inputEl,
      isFocused,
      cls,
    };
  }
})
</script>

<template>
  <div class="br-input" :class="cls">
    <span @click="inputEl.focus()" class="br-input__prefix">https://</span>
    <input
        @focus="isFocused = true"
        @blur="isFocused = false"
        ref="inputEl"
        class="br-input__input"
        type="text"
        placeholder="Type your text here..."
    >
    <span @click="inputEl.focus()" class="br-input__postfix">@gmail.com</span>
  </div>
</template>

<style>
:root {
  --component-border: #CDD9ED;
  --input-color: #99A3BA;
  --input-placeholder: #CBD1DC;
  --appends-bg: #EEF4FF;
  --appends-active-bg: #678EFE;
  --appends-color: #99A3BA;
  --appends-active-color: #fff;
  --component-border-focus: #275EFE;
}
.br-input__prefix, .br-input__postfix, .br-input__input {
  padding: 8px 16px;
}
.br-input {
  display: flex;
  line-height: 25px;
  font-weight: 500;
  border-radius: 6px;
  border: 1px solid var(--component-border);
  transition: border .3s ease;
}
.br-input-focused {
  border: 1px solid var(--component-border-focus);
}

.br-input__input {
  flex: 1;
  color: var(--input-color);
  border: none;
}
.br-input__input:focus {
  outline: none;
}
.br-input__input::placeholder {
  color: var(--input-placeholder);
}

.br-input__prefix, .br-input__postfix {
  background: var(--appends-bg);
  color: var(--appends-color);
  transition: background .3s ease, border .3s ease, color .3s;
}
.br-input__prefix {
  border-right: 1px var(--component-border) solid;
}
.br-input-focused .br-input__prefix, .br-input-focused .br-input__postfix {
  background: var(--appends-active-bg);
  color: var(--appends-active-color);
}
.br-input__postfix {
  border-left: 1px var(--component-border) solid;
}
</style>
