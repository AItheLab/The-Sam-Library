<script setup lang="ts">
import SAMButton from './components/btn/sam-btn.vue'
import SAMCard from './components/card/sam-card.vue'
import SAMCalendar from './components/calendar/sam-calendar.vue'

const handleClick = () => {
  console.log('Button clicked')
}

const toggleTheme = () => {
  const body = document.body;
  const currentTheme = body.getAttribute('data-theme');
  const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
  body.setAttribute('data-theme', newTheme);
}

const handleLeftClick = () => {
  console.log('Left button clicked')
}

const handleRightClick = () => {
  console.log('Right button clicked')
}
</script>

<template>
  <div class="app">
    <button class="themeSwitch" @click="toggleTheme">Toggle theme</button>
    <div>
      <SAMButton label="Click me" type="filled" @click="handleClick" />
      <SAMButton label="Click me" type="outlined" @click="handleClick" />
      <SAMButton label="Click me" type="text" @click="handleClick" />
      <SAMButton label="Click me" type="elevated" @click="handleClick" />
      <SAMButton label="Click me" type="tonal" @click="handleClick" />
    </div>
    <br>
    <div>
      <SAMButton label="Click me" type="filled" icon="mdi-light:home" @click="handleClick" />
      <SAMButton label="Click me" type="outlined" icon="mdi-light:home" @click="handleClick" />
      <SAMButton label="Click me" type="text" icon="mdi-light:home" @click="handleClick" />
      <SAMButton label="Click me" type="elevated" icon="mdi-light:home" @click="handleClick" />
      <SAMButton label="Click me" type="tonal" icon="mdi-light:home" @click="handleClick" />
    </div>
    <br>
    <div class="grid-container">
      <SAMCard
        :avatarSection="true"
        avatarName="John Doe"
        avatarSubtitle="Developer"
        avatarImage="src/assets/avatar.webp"
        imageUrl="src/assets/background_moto.webp"
        title="Card Title"
        subtitle="Card Subtitle"
        text="This is the main content of the card."
        :buttonSection="true"
        buttonLeftLabel="Accept"
        buttonLeftType="outlined"
        buttonRightLabel="Decline"
        buttonRightType="filled"
        @buttonLeftEventClick="handleLeftClick"
        @buttonRightEventClick="handleRightClick"
        type="type1"
      />
      <SAMCard
        :avatarSection="true"
        avatarName="John Doe"
        avatarSubtitle="Developer"
        avatarImage="src/assets/avatar.webp"
        imageUrl="src/assets/background_moto.webp"
        title="Card Title"
        subtitle="Card Subtitle"
        text="This is the main content of the card."
        :buttonSection="true"
        buttonLeftLabel="Accept"
        buttonLeftType="outlined"
        buttonRightLabel="Decline"
        buttonRightType="filled"
        @buttonLeftEventClick="handleLeftClick"
        @buttonRightEventClick="handleRightClick"
        type="type1"
        :headerOverImage="true"
      />

      <SAMCard
        :avatarSection="true"
        avatarName="John Doe"
        avatarSubtitle="Developer"
        avatarImage="src/assets/avatar.webp"
        imageUrl="src/assets/background_moto.webp"
        title="Card Title"
        subtitle="Card Subtitle"
        text="This is the main content of the card."
        :buttonSection="true"
        buttonLeftLabel="Accept"
        buttonLeftType="outlined"
        buttonRightLabel="Decline"
        buttonRightType="filled"
        @buttonLeftEventClick="handleLeftClick"
        @buttonRightEventClick="handleRightClick"
        type="type2"
      />

      <SAMCard
        :avatarSection="true"
        avatarName="John Doe"
        avatarSubtitle="Developer"
        avatarImage="src/assets/avatar.webp"
        imageUrl="src/assets/background_moto.webp"
        title="Card Title"
        subtitle="Card Subtitle"
        text="This is the main content of the card."
        :buttonSection="true"
        buttonLeftLabel="Accept"
        buttonLeftType="outlined"
        buttonRightLabel="Decline"
        buttonRightType="filled"
        @buttonLeftEventClick="handleLeftClick"
        @buttonRightEventClick="handleRightClick"
        type="type3"
        :headerOverImage="true"
      />

    </div>

    <div>
      <SAMCalendar @date-selected="handleDateSelected" locale="en" theme="light" />
    </div>
    
  </div>
</template>

<style scoped>
.themeSwitch {
  position: absolute;
  top: 0;
  right: 0;
}
.app {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  min-height: 100vh;
  background-color: #f0f0f0;
}
body[data-theme="dark"] .app {
  background-color: #333; /* Cambia esto al color oscuro que prefieras */
}
.grid-container {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 40px;
  padding: 40px;
}

@media (max-width: 1024px) {
  .grid-container {
    grid-template-columns: repeat(auto-fill, minmax(450px, 1fr));
    padding: 20px;
  }
}

@media (max-width: 768px) {
  .grid-container {
    grid-template-columns: 1fr;
    padding: 10px;
  }
}
</style>