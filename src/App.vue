<template>
  <div>
    <h1>Proverbio del Día</h1>
    <p>{{ formattedDate }}</p>
    <vue-plyr>
      <audio controls playsinline>
        <source :src="audioSrc" type="audio/mp3">
        Your browser does not support the audio element.
      </audio>
    </vue-plyr>
  </div>
</template>

<script lang="ts">
const dateInformation = new Date();

export default {
  data() {
    return {
      date: dateInformation,
      audioSrc:''
    };
  },
  computed: {
    dailyAudio() {
      const dayOfMonth = this.date.getDate();
      this.audioSrc = `/proverbios/${dayOfMonth} Pista.mp3`;
    },
    formattedDate() {
      const options = {
        weekday: 'long',
        day: 'numeric',
        month: 'long',
        year: 'numeric',
      };
      return this.date.toLocaleDateString('es-ES', options as Intl.DateTimeFormatOptions);
    },
  },
};
</script>

<style scoped></style>
