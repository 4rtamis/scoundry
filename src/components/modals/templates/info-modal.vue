<template>
    <ModalFrame>
        <template v-slot:header>
            <ModalHeader>
                <h3>{{ props.title }}</h3>
            </ModalHeader>
        </template>
        <template v-slot:content>
            <div class="info">
                <p v-html="props.message"></p>

                <div class="row wrap center">
                    <button
                        class="btn"
                        @click="props.onConfirm || ModalController.close()"
                    >
                        <span>{{ props.confirmText || 'Ok' }}</span>
                    </button>
                </div>
            </div>
        </template>
    </ModalFrame>
</template>

<script setup lang="ts">
import ModalFrame from '@/components/modals/modal-frame.vue';
import ModalHeader from '@/components/modals/modal-header.vue';
import ModalController from '@/controllers/modal-controller';

const props = defineProps<{
    title: string;
    message: string;
    onConfirm: () => void;
    confirmText?: string;
}>();
</script>

<style scoped lang="scss">
.info {
    display: flex;
    flex-direction: column;
    gap: 1.6rem;
    height: 100%;
    justify-content: space-between;
}
</style>
