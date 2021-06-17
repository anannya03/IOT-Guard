<template>
  <div class="mt-5 container">
    <div class="buttons is-centered">
      <!-- Guide button -->
      <a class="button" @click="isGuideActive = true">
        <span class="is-large mr-2">
          <i class="fas fa-info-circle custom-text-dark"></i>
        </span>
        <span class="custom-text-dark custom-regular-text">Guide</span>
      </a>
      <!-- Github button -->
      <a class="button" href="https://github.com/anannya03/IOT-Guard">
        <span class="is-large mr-2">
          <i class="fab fa-github custom-text-dark"></i>
        </span>
        <span class="custom-text-dark custom-regular-text">Source</span>
      </a>
    </div>
    <!-- Display the guide if isGuideActive is true -->
    <div class="modal" v-bind:class="{ 'is-active': isGuideActive }">
      <div
        class="modal-background"
        @click="isGuideActive = !isGuideActive"
      ></div>
      <div class="modal-content">
        <div class="notification custom-notification custom-text-dark">
          <button
            class="delete"
            aria-label="close"
            @click="isGuideActive = !isGuideActive"
          ></button>
          <strong>
            Hey there! here's a little something about this project.
          </strong>
          <br />
          <br />
          Indoor Air Quality (IAQ), of late, has been an increasing cause for
          concern due to its worrisome effects on human health. Indoor
          surroundings undoubtedly contain pollutants and their presence has
          only increased in recent decades due to factors like constructions,
          furnishings, cooking fuels, personal care products, pesticides,
          household cleaners and more. Multiple studies have shown time and
          again that we humans spend a large amount of our time indoors. Even
          more concerning is the fact that the ongoing COVID-19 pandemic is
          forcing us to stay indoors for longer than ever before. This calls for
          an analysis of our indoor surroundings, the silent pollutants present
          within and their corresponding effects on our health.
          <br />
          <br />
          This project is aimed at enabling indoor air quality monitoring for an
          extremely low cost within homes and small offices. As a result, the
          system is capable of sensing the presence of taint gases like CO, CO2,
          CH4, SO2, Acetone and NH3.
          <br />
          <br />
          To find the concentrations of particular gases, simply click on the
          same within the legend. In case the thresholds of any of the gases
          given in the graph are breached, an alert will be sent to your email
          address.
          <br />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Info",
  data: function() {
    return {
      isGuideActive: true,
    };
  },
};
</script>

<style>
.button {
  border: none;
  box-shadow: -0.3rem 0.3rem 0 0 #ece8d9;
  text-decoration: none;
}
.button:focus {
  border: none;
  box-shadow: -0.3rem 0.3rem 0 0 #ece8d9;
}
.button:active {
  border: none;
  box-shadow: none;
}
.is-large {
  height: 100%;
  width: 100%;
}
.custom-notification {
  background-color: #faf6e9;
}
</style>
