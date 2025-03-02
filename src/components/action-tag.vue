<template>
    <div
        class="action-tag"
        :class="{ disabled: value == 0 }"
        :style="{
            backgroundColor: color,
            borderColor: color,
        }"
    >
        <ul class="circles-list">
            <li v-for="i in value" :key="i" :style="{ color }"></li>
            <li class="empty" v-if="value == 0" :style="{ color }"></li>
        </ul>
        <p class="label">{{ $t(`Actions.${capitalize(action)}.label`) }}</p>
    </div>
</template>

<script lang="ts" setup>
import { getAttribute, getAttributeColor } from '@/util/action-util';
import { capitalize } from '@/util/string-util';
import { computed } from 'vue';

const props = defineProps<{
    action: string;
    value: number;
}>();

const color = computed(() => {
    const attribute = getAttribute(props.action)!;
    return getAttributeColor(attribute);
});
</script>

<style lang="scss" scoped>
.action-tag {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0rem 0.8rem 0rem 0.6rem;
    height: 2rem;
    border-radius: 99px;
    color: var(--color-on-surface);
    border: 1px solid currentColor;

    &.disabled {
        opacity: 0.7;
    }

    ul.circles-list {
        display: flex;
        margin-right: 0.6rem;

        > li {
            width: 0.8rem;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;

            &::before {
                content: '';
                position: absolute;
                display: block;
                width: 1.25rem;
                height: 1.25rem;
                border-radius: 50%;
                background-color: currentColor;
            }

            &::after {
                content: '';
                position: absolute;
                width: 1rem;
                height: 1rem;
                border-radius: 50%;
                background-color: var(--color-on-surface);
            }

            // Empty: Show an empty circle
            &.empty::before {
                display: none;
            }

            &.empty::after {
                background-color: transparent;
                border: 0.1rem solid var(--color-on-surface);
            }
        }
    }

    p {
        position: relative;
        top: 0.05rem;
    }
}

@media (max-width: 768px) {
    .action-tag {
        padding: 0 0.8rem 0 0.8rem;
    }
}
</style>
