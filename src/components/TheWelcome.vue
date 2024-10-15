<script setup>
import { ref } from "vue";

const inputUnit = ref("");
const kilograms = ref(0);
const pounds = ref(0);
const meters = ref(0);
const centimeters = ref(0);
const inches = ref(0);
const millimeters = ref(0);
const feet = ref(0);
const gallons = ref(0);
const litres = ref(0);

const unitConverter = () => {
  if (inputUnit.value === "kilograms") {
    kilograms.value = pounds.value / 2.20462;
  }
  if (inputUnit.value === "pounds") {
    pounds.value = kilograms.value * 2.20462;
  }
  if (inputUnit.value === "meters") {
    meters.value = centimeters.value * 100;
  }
  if (inputUnit.value === "centimeters") {
    centimeters.value = meters.value / 100;
  }

  if (inputUnit.value === "inches") {
    inches.value = centimeters.value * 2.54;
  }
  if (inputUnit.value === "millimeters") {
    millimeters.value = inches.value * 25.4;
  }
  if (inputUnit.value === "feet") {
    feet.value = meters.value / 0.3048;
  }
  if (inputUnit.value === "gallons") {
    gallons.value = litres.value * 0.264172;
  }
  if (inputUnit.value === "litres") {
    litres.value = gallons.value * 3.78541;
  }
};
</script>

<style scoped></style>

<template>
  <div>
    <!-- Responsive Navigation Bar -->
    <nav class="bg-indigo-600 p-4">
      <div class="container mx-auto flex justify-between items-center">
        <!-- Logo -->
        <a href="#" class="text-white text-lg font-semibold">Unit Converter</a>
      </div>
    </nav>

    <!-- Explanation Card -->
    <div class="container mx-auto mt-8">
      <div class="bg-white shadow-md rounded-lg p-6 max-w-4xl mx-auto">
        <h2 class="text-lg font-semibold text-indigo-600 mb-4">
          How the Unit Converter Works
        </h2>
        <p class="text-gray-700">
          This unit converter allows you to convert between various units of
          weight and length. Simply select the unit you'd like to convert, enter
          the value, and the corresponding conversion will be automatically
          calculated and displayed.
        </p>
        <ul class="mt-4 space-y-2 list-disc list-inside">
          <li>Weight conversions between kilograms and pounds.</li>
          <li>
            Length conversions between meters, centimeters, millimeters, feet,
            and inches.
          </li>
          <li>
            Volume conversions between gallons, litres.
          </li>
          <li>
            All conversions are performed in real-time, ensuring quick and
            accurate results.
          </li>
        </ul>
        <p class="text-gray-700 mt-4">Give it a try below!</p>
      </div>
    </div>

    <!-- Main Unit Converter Form -->
    <div class="min-h-screen bg-gray-100 flex items-center justify-center">
      <div class="bg-white shadow-md rounded-lg p-6 w-full max-w-md mt-8">
        <form method="post" @submit.prevent="unitConverter" class="space-y-6">
          <div class="flex flex-col">
            <label for="inputUnit" class="text-sm font-semibold text-gray-700"
              >Enter unit to convert:</label
            >
            <textarea
              id="inputUnit"
              v-model="inputUnit"
              required
              placeholder="Enter 'kilograms', 'pounds', 'meters', 'centimeters', 'millimeters', 'inches', or 'feet' or 'gallons' or 'litres'"
              class="mt-1 py-2 px-4 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full"></textarea>
          </div>

          <!-- Kilograms to Pounds -->
          <div v-if="inputUnit === 'kilograms'" class="space-y-4">
            <div class="flex flex-col">
              <label for="kilograms" class="text-sm font-semibold text-gray-700"
                >Kilograms:</label
              >
              <input
                type="number"
                id="kilograms"
                v-model="kilograms"
                min="0"
                required
                class="mt-1 py-2 px-4 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
            <div class="flex flex-col">
              <label for="pounds" class="text-sm font-semibold text-gray-700"
                >Pounds:</label
              >
              <input
                type="number"
                id="pounds"
                :value="kilograms * 2.20462"
                disabled
                class="mt-1 py-2 px-4 bg-gray-100 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
          </div>

          <!-- Pounds to Kilograms -->
          <div v-else-if="inputUnit === 'pounds'" class="space-y-4">
            <div class="flex flex-col">
              <label for="pounds" class="text-sm font-semibold text-gray-700"
                >Pounds:</label
              >
              <input
                type="number"
                id="pounds"
                v-model="pounds"
                min="0"
                required
                class="mt-1 py-2 px-4 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
            <div class="flex flex-col">
              <label for="kilograms" class="text-sm font-semibold text-gray-700"
                >Kilograms:</label
              >
              <input
                type="number"
                id="kilograms"
                :value="pounds / 2.20462"
                disabled
                class="mt-1 py-2 px-4 bg-gray-100 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
          </div>

          <!-- Meters to Centimeters and Feet -->
          <div v-else-if="inputUnit === 'meters'" class="space-y-4">
            <div class="flex flex-col">
              <label for="meters" class="text-sm font-semibold text-gray-700"
                >Meters:</label
              >
              <input
                type="number"
                id="meters"
                v-model="meters"
                min="0"
                required
                class="mt-1 py-2 px-4 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
            <div class="flex flex-col">
              <label
                for="centimeters"
                class="text-sm font-semibold text-gray-700"
                >Centimeters:</label
              >
              <input
                type="number"
                id="centimeters"
                :value="meters * 100"
                disabled
                class="mt-1 py-2 px-4 bg-gray-100 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
            <div class="flex flex-col">
              <label for="feet" class="text-sm font-semibold text-gray-700"
                >Feet:</label
              >
              <input
                type="number"
                id="feet"
                :value="meters * 3.28084"
                disabled
                class="mt-1 py-2 px-4 bg-gray-100 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
          </div>

          <!-- Centimeters to Meters -->
          <div v-else-if="inputUnit === 'centimeters'" class="space-y-4">
            <div class="flex flex-col">
              <label
                for="centimeters"
                class="text-sm font-semibold text-gray-700"
                >Centimeters:</label
              >
              <input
                type="number"
                id="centimeters"
                v-model="centimeters"
                min="0"
                required
                class="mt-1 py-2 px-4 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
            <div class="flex flex-col">
              <label for="meters" class="text-sm font-semibold text-gray-700"
                >Meters:</label
              >
              <input
                type="number"
                id="meters"
                :value="centimeters / 100"
                disabled
                class="mt-1 py-2 px-4 bg-gray-100 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
          </div>

          <!-- Millimeters to Inches -->
          <div v-else-if="inputUnit === 'millimeters'" class="space-y-4">
            <div class="flex flex-col">
              <label
                for="millimeters"
                class="text-sm font-semibold text-gray-700"
                >Millimeters:</label
              >
              <input
                type="number"
                id="millimeters"
                v-model="millimeters"
                min="0"
                required
                class="mt-1 py-2 px-4 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
            <div class="flex flex-col">
              <label for="inches" class="text-sm font-semibold text-gray-700"
                >Inches:</label
              >
              <input
                type="number"
                id="inches"
                :value="millimeters / 25.4"
                disabled
                class="mt-1 py-2 px-4 bg-gray-100 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
          </div>

          <!-- Inches to Millimeters -->
          <div v-else-if="inputUnit === 'inches'" class="space-y-4">
            <div class="flex flex-col">
              <label for="inches" class="text-sm font-semibold text-gray-700"
                >Inches:</label
              >
              <input
                type="number"
                id="inches"
                v-model="inches"
                min="0"
                required
                class="mt-1 py-2 px-4 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
            <div class="flex flex-col">
              <label
                for="millimeters"
                class="text-sm font-semibold text-gray-700"
                >Millimeters:</label
              >
              <input
                type="number"
                id="millimeters"
                :value="inches * 25.4"
                disabled
                class="mt-1 py-2 px-4 bg-gray-100 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
          </div>
          <!-- Feet to Meters -->
          <div v-else-if="inputUnit === 'feet'" class="space-y-4">
            <div class="flex flex-col">
              <label for="feet" class="text-sm font-semibold text-gray-700"
                >Feet:</label
              >
              <input
                type="number"
                id="feet"
                v-model="feet"
                min="0"
                required
                class="mt-1 py-2 px-4 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
            <div class="flex flex-col">
              <label for="meters" class="text-sm font-semibold text-gray-700"
                >Meters:</label
              >
              <input
                type="number"
                id="meters"
                :value="feet / 3.28084"
                disabled
                class="mt-1 py-2 px-4 bg-gray-100 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
          </div>

          <!-- Gallons to Liters -->
          <div v-else-if="inputUnit === 'gallons'" class="space-y-4">
            <div class="flex flex-col">
              <label for="gallons" class="text-sm font-semibold text-gray-700"
                >Gallons:</label
              >
              <input
                type="number"
                id="gallons"
                v-model="gallons"
                min="0"
                required
                class="mt-1 py-2 px-4 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
            <div class="flex flex-col">
              <label for="liters" class="text-sm font-semibold text-gray-700"
                >Liters:</label
              >
              <input
                type="number"
                id="liters"
                :value="gallons * 3.78541"
                disabled
                class="mt-1 py-2 px-4 bg-gray-100 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
          </div>

          <!-- Liters to Gallons -->
          <div v-else-if="inputUnit === 'litres'" class="space-y-4">
            <div class="flex flex-col">
              <label for="liters" class="text-sm font-semibold text-gray-700"
                >Liters:</label
              >
              <input
                type="number"
                id="liters"
                v-model="litres"
                min="0"
                required
                class="mt-1 py-2 px-4 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
            <div class="flex flex-col">
              <label for="gallons" class="text-sm font-semibold text-gray-700"
                >Gallons:</label
              >
              <input
                type="number"
                id="gallons"
                :value="litres / 3.78541"
                disabled
                class="mt-1 py-2 px-4 bg-gray-100 border border-gray-300 rounded-lg shadow-sm focus:ring focus:ring-indigo-300 focus:border-indigo-500 outline-none transition duration-150 ease-in-out w-full" />
            </div>
          </div>

          <!-- Submit Button -->
          <button
            type="submit"
            class="w-full py-2 px-4 bg-indigo-600 text-white rounded-lg font-semibold shadow-md hover:bg-indigo-500 focus:outline-none focus:ring-2 focus:ring-indigo-300 transition duration-150 ease-in-out">
            Convert
          </button>
        </form>
      </div>
    </div>
  </div>
</template>
