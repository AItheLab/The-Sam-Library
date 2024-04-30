<template>
    <div :class="[{ 'sam-card--has-image': imageUrl }, `sam-card sam-card--${type}`]">
        <div 
            v-if="avatarSection" 
            class="sam-card__avatar" 
            :class="{ 'sam-card__avatar--inside-image': headerOverImage }"
            >
            <img v-if="avatarImage" :src="avatarImage" alt="Avatar" class="sam-card__avatar-image">
            <div>
                <h3 v-if="avatarName" class="sam-card__avatar-name">{{ avatarName }}</h3>
                <p v-if="avatarSubtitle" class="sam-card__avatar-subtitle">{{ avatarSubtitle }}</p>
            </div>
        </div>

        <img v-if="imageUrl" :src="imageUrl" alt="Card Image" class="sam-card__image">

        <div class="sam-card__content">
            <h2 v-if="title">{{ title }}</h2>
            <h3 v-if="subtitle">{{ subtitle }}</h3>
            <p v-if="text">{{ text }}</p>
        </div>

        <div v-if="buttonSection" class="sam-card__actions">
            <SAMButton v-if="buttonLeftLabel" :label="buttonLeftLabel" :type="buttonLeftType"
                @click="buttonLeftEventClick" />
            <SAMButton v-if="buttonRightLabel" :label="buttonRightLabel" :type="buttonRightType"
                @click="buttonRightEventClick" />
        </div>
    </div>
</template>
  
  <script setup lang="ts">
  import { withDefaults, defineProps } from 'vue'
import SAMButton from '../btn/sam-btn.vue'

interface IProps {
    avatarSection?: boolean;
    avatarName?: string;
    avatarSubtitle?: string;
    avatarImage?: string;
    imageUrl?: string;
    title?: string;
    subtitle?: string;
    text?: string;
    buttonSection?: boolean;
    buttonLeftLabel?: string;
    buttonLeftType?: string;
    buttonRightLabel?: string;
    buttonRightType?: string;
    type?: string
    headerOverImage?: boolean
}

withDefaults(defineProps<IProps>(), {
    avatarSection: false,
    avatarName: '',
    avatarSubtitle: '',
    avatarImage: '',
    imageUrl: '',
    title: '',
    subtitle: '',
    text: '',
    buttonSection: false,
    buttonLeftLabel: '',
    buttonLeftType: 'filled',
    buttonRightLabel: '',
    buttonRightType: 'outlined',
    type: 'type1' // Default type is type1
})

const buttonLeftEventClick = () => {
    console.log('Left button clicked')
};
const buttonRightEventClick = () => {
    console.log('Right button clicked')
};
  </script>
  
  <style scoped lang="scss" src="./sam-card.scss"/>
  