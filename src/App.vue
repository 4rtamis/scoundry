<template>
    <div class="app-layout">
        <div class="pattern"></div>
        <router-view name="page"></router-view>
        <the-modal-container />
    </div>
</template>

<script setup lang="ts">
import TheModalContainer from './components/modals/the-modal-container.vue';
import { initializeI18nInstance } from './i18n/locale';

initializeI18nInstance();
</script>

<style lang="scss">
@use './assets/scss/reset.scss';
@use './assets/scss/styles.scss';

.app-layout {
    position: relative;
    background-color: var(--color-surface);
    height: 100vh;
    min-height: -webkit-fill-available;
    overflow: hidden;
    display: flex;
    flex-direction: column;
}

.page {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

.pattern {
    width: 100%;
    height: 100vh;
    min-height: -webkit-fill-available;

    opacity: 0.1;

    background-image: url('/assets/images/floral.jpg');
    background-size: 20rem;
    background-position: center;
    background-attachment: fixed;
    background-repeat: repeat;
}
</style>
