<!--<script setup>-->
<!--import { ref, computed, onMounted, onUnmounted } from 'vue';-->


<!--const props = defineProps({-->
<!--  title: { type: String, default: '' },-->
<!--  placement: { type: String, default: 'top' } // 'top' | 'bottom' | 'left' | 'right'-->
<!--});-->

<!--const placement = computed(() => props.placement || 'top');-->
<!--const visible = ref(false);-->
<!--const root = ref(null);-->

<!--const hide = () => (visible.value = false);-->
<!--const show = () => (visible.value = true);-->
<!--const toggle = () => (visible.value = !visible.value);-->

<!--// 点击页面其它区域关闭（兼容手机）-->
<!--const handleOutside = (e) => {-->
<!--  if (!root.value) return;-->
<!--  if (!root.value.contains(e.target)) {-->
<!--    hide();-->
<!--  }-->
<!--};-->

<!--onMounted(() => {-->
<!--  document.addEventListener('click', handleOutside, true);-->
<!--  document.addEventListener('touchstart', handleOutside, true);-->
<!--});-->

<!--onUnmounted(() => {-->
<!--  document.removeEventListener('click', handleOutside, true);-->
<!--  document.removeEventListener('touchstart', handleOutside, true);-->
<!--});-->
<!--</script>-->

<!--<template>-->
<!--  <span-->
<!--    ref="root"-->
<!--    class="ez-tooltip"-->
<!--    :class="[`placement-` + placement]"-->
<!--    @mouseenter="show"-->
<!--    @mouseleave="hide"-->
<!--  >-->
<!--    &lt;!&ndash; 触发器：默认是一个问号，也可通过 named slot 覆盖 &ndash;&gt;-->
<!--    <slot name="trigger">-->
<!--      <span-->
<!--        class="tip-trigger"-->
<!--        role="button"-->
<!--        tabindex="0"-->
<!--        aria-label="帮助"-->
<!--        @click.stop="toggle"-->
<!--        @keydown.enter.prevent="toggle"-->
<!--      >-->
<!--        <img src="./question.svg" alt="?" style="width: 18px; height: 18px;" />-->
<!--      </span>-->
<!--    </slot>-->

<!--    <transition name="fade">-->
<!--      <div v-show="visible" class="tip-content" role="tooltip">-->
<!--        <slot>-->
<!--          {{ props.title }}-->
<!--        </slot>-->
<!--        <span class="tip-arrow" />-->
<!--      </div>-->
<!--    </transition>-->
<!--  </span>-->
<!--</template>-->

<!--<style scoped lang="scss">-->
<!--.ez-tooltip {-->
<!--  position: relative;-->
<!--  display: inline-flex;-->
<!--  align-items: center;-->
<!--}-->

<!--.tip-trigger {-->
<!--  position: relative;-->
<!--  display: inline-flex;-->
<!--  align-items: center;-->
<!--  justify-content: center;-->
<!--  width: 18px;-->
<!--  height: 18px;-->
<!--  margin-left: 6px;-->
<!--  border-radius: 50%;-->
<!--  font-size: 12px;-->
<!--  line-height: 18px;-->
<!--  cursor: pointer;-->
<!--  user-select: none;-->

<!--}-->

<!--.tip-content {-->
<!--  position: absolute;-->
<!--  z-index: 1000;-->
<!--  min-width: 160px;-->
<!--  max-width: 280px;-->
<!--  padding: 8px 10px;-->
<!--  border-radius: 8px;-->
<!--  font-size: 12px;-->
<!--  color: #fff;-->
<!--  background: rgba(0,0,0,.85);-->
<!--  box-shadow: 0 4px 12px rgba(0,0,0,.15);-->
<!--  word-break: break-word;-->
<!--  white-space: normal;-->
<!--}-->

<!--/* 方向与箭头 */-->
<!--.placement-top .tip-content { bottom: 125%; left: 50%; transform: translateX(-50%); }-->
<!--.placement-bottom .tip-content { top: 125%; left: 50%; transform: translateX(-50%); }-->
<!--.placement-left .tip-content { right: 125%; top: 50%; transform: translateY(-50%); }-->
<!--.placement-right .tip-content { left: 125%; top: 50%; transform: translateY(-50%); }-->

<!--.tip-arrow {-->
<!--  position: absolute;-->
<!--  width: 0; height: 0;-->
<!--  border-style: solid;-->
<!--}-->

<!--.placement-top .tip-arrow {-->
<!--  bottom: -6px; left: 50%; transform: translateX(-50%);-->
<!--  border-width: 6px 6px 0 6px;-->
<!--  border-color: rgba(0,0,0,.85) transparent transparent transparent;-->
<!--}-->
<!--.placement-bottom .tip-arrow {-->
<!--  top: -6px; left: 50%; transform: translateX(-50%);-->
<!--  border-width: 0 6px 6px 6px;-->
<!--  border-color: transparent transparent rgba(0,0,0,.85) transparent;-->
<!--}-->
<!--.placement-left .tip-arrow {-->
<!--  right: -6px; top: 50%; transform: translateY(-50%);-->
<!--  border-width: 6px 0 6px 6px;-->
<!--  border-color: transparent transparent transparent rgba(0,0,0,.85);-->
<!--}-->
<!--.placement-right .tip-arrow {-->
<!--  left: -6px; top: 50%; transform: translateY(-50%);-->
<!--  border-width: 6px 6px 6px 0;-->
<!--  border-color: transparent rgba(0,0,0,.85) transparent transparent;-->
<!--}-->

<!--/* 动画 */-->
<!--.fade-enter-active, .fade-leave-active { transition: opacity .18s ease; }-->
<!--.fade-enter-from, .fade-leave-to { opacity: 0; }-->
<!--</style>-->