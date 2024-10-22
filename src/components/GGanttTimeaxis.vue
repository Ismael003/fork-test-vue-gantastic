<template>
  <div class="g-timeaxis">
    <div class="g-timeunits-container">
      <button class="button-icon left-arrow" @click="change_month('left')"><svg xmlns="http://www.w3.org/2000/svg"
          height="100%" viewBox="0 -960 960 960" width="24">
          <path d="m313-440 224 224-57 56-320-320 320-320 57 56-224 224h487v80H313Z" />
        </svg></button>
      <div v-for="({ label, value, date, width }, index) in timeaxisUnits.upperUnits" :key="label"
        class="g-upper-timeunit" :style="{
          background: index % 2 === 0 ? colors.primary : colors.secondary,
          color: colors.text,
          width
        }">
        <slot name="upper-timeunit" :label="label" :value="value" :date="date">
          {{ label }}
        </slot>
      </div>
      <button class="button-icon right-arrow" @click="change_month('right')"><svg xmlns="http://www.w3.org/2000/svg"
          height="100%" viewBox="0 -960 960 960" width="24">
          <path d="M647-440H160v-80h487L423-744l57-56 320 320-320 320-57-56 224-224Z" />
        </svg></button>
    </div>

    <div class="g-timeunits-container">
      <div v-for="({ label, value, date, width }, index) in timeaxisUnits.lowerUnits" :key="label" class="g-timeunit"
        :style="{
          background: index % 2 === 0 ? colors.ternary : colors.quartenary,
          color: colors.text,
          flexDirection: precision === 'hour' ? 'column' : 'row',
          alignItems: precision === 'hour' ? '' : 'center',
          width
        }">
        <slot name="timeunit" :label="label" :value="value" :date="date">
          {{ label }}
        </slot>
        <div v-if="precision === 'hour'" class="g-timeaxis-hour-pin" :style="{ background: colors.text }" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import provideConfig from "../provider/provideConfig.js"
import useTimeaxisUnits from "../composables/useTimeaxisUnits.js"

const { precision, colors } = provideConfig()
const { timeaxisUnits } = useTimeaxisUnits()

const emit = defineEmits<{
  (e: "set_month", value: { set_type: string; }): void

}>()

const change_month = (typeChange: string) => {
  emit("set_month", { set_type: typeChange })
}

</script>

<style>
.g-timeaxis {
  position: sticky;
  top: 0;
  width: 100%;
  height: 8vh;
  min-height: 75px;
  background: white;
  z-index: 4;
  box-shadow: 0px 1px 3px 2px rgba(50, 50, 50, 0.5);
  display: flex;
  flex-direction: column;
  padding-top: 0px;
  box-shadow: none;
}

.g-timeunits-container {
  display: flex;
  width: 100%;
  height: 50%;
  background-color: rgb(238, 238, 238);
}

.g-timeunit {
  height: 100%;
  font-size: 65%;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.g-upper-timeunit {
  display: flex;
  height: 100%;
  justify-content: center;
  align-items: center;
}

.g-timeaxis-hour-pin {
  width: 1px;
  height: 10px;
}

.button-icon {
  background-color: rgb(238, 238, 238);
  border: none;
  cursor: pointer;
  font-size: 0;
  /* Oculta el texto del botón */
  padding: 0;
  /* Elimina el espacio adicional dentro del botón */
  position: relative;
  width: 30px;
  /* Ancho del botón (ajusta según sea necesario) */
  height: 30px;
  /* Altura del botón (ajusta según sea necesario) */
}

/* Estilo para el botón con flecha izquierda */
.left-arrow {
  background-color: rgb(238, 238, 238);
  border: none;
  cursor: pointer;
  font-size: 0;
  padding: 0;
  position: relative;
  width: 30px;
  height: 30px;
  padding-top: 10px;
}

.right-arrow {
  background-color: rgb(238, 238, 238);
  border: none;
  cursor: pointer;
  font-size: 0;
  padding: 0;
  position: relative;
  width: 30px;
  height: 30px;
  padding-top: 10px;
}
</style>
