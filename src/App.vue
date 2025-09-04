<script setup>
import { ref } from 'vue'

const accordioniItems = ref([
  { title: 'Workflow Details', content: 'Content for Workflow Details' },
  { title: 'Input and Output Parameters', content: 'Input and Output Parameters' },
  { title: 'Schema Validation', content: 'Schema Validation' },
  { title: 'Workflow Configuration', content: 'Content for Workflow Configuration' },
  { title: 'Advanced Settings', content: 'Content for Advanced Settings' },
])

const activeItem = ref(null)

const toggleAccordion = (index) => {
  activeItem.value = activeItem.value === index ? null : index
}
</script>

<template>
  <main>
    <div class="first-preview">
      <div class="start-text">Start</div>
      <button class="add-button">+</button>

      <div class="vertical-line" />

      <!-- First Card -->
      <div class="card">
        <div class="card-header">
          <div>
            <div id>perkalian</div>
            <button>inline</button>
          </div>
          <div>perkalian_ref</div>
        </div>
        <div class="card-body">
          <textarea name="inputTextarea1" id="inputTextarea1" />
        </div>
      </div>

      <button class="add-button">+</button>
      <div class="vertical-line" />

      <!-- Second Card -->
      <div class="card">
        <div class="card-header">
          <div>
            <div id>penjumlahan</div>
            <button>inline</button>
          </div>
          <div>penjumlahan_ref</div>
        </div>
        <div class="card-body">
          <textarea name="inputTextarea2" id="inputTextarea2" />
        </div>
      </div>

      <button class="add-button">+</button>
      <div class="vertical-line" />

      <div class="end-text">End</div>
    </div>

    <div class="second-preview">
      <div class="top-navbar">
        <div>Workflow</div>
        <div>Task</div>
        <div>Code</div>
        <div>Run</div>
        <div>Dependencies</div>
      </div>

      <div class="accordion-container">
        <div v-for="(accordionItem, index) in accordioniItems" :key="index" class="accordion-item">
          <div class="accordion-header" @click="toggleAccordion(index)">
            {{ accordionItem.title }}
          </div>
          <div v-show="activeItem === index" class="accordion-content">
            {{ accordionItem.content }}
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  display: grid;
}

.accordion-container {
  width: 100%;
  padding: 48px 32px;
}

.accordion-item {
  border-bottom: 2px solid rgba(235, 235, 235, 0.64);
}

.accordion-item:last-child {
  border-bottom: none;
}

.accordion-header {
  background-color: #ffffff;
  color: #444;
  cursor: pointer;
  font-weight: 700;
  font-size: 16px;
  padding: 18px;
  width: 100%;
  text-align: left;
  border: none;
  outline: none;
  transition: 0.4s;
}

.active,
.accordion-header:hover {
  background-color: #ccc;
}

.accordion-content {
  padding: 18px;
  background-color: white;
  overflow: hidden;
}

.first-preview {
  padding: 32px;
}

.top-navbar {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  width: 100%;
  padding: 18px;
  background-color: #ffffff;
  border-bottom: 2px solid rgba(235, 235, 235, 0.64);
  text-align: center;
}

.first-preview,
.second-preview {
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 1.5px solid black;
}

.start-text,
.end-text {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  border: 3px solid grey;
  display: flex;
  justify-content: center;
  align-items: center;
}

.add-button {
  width: 18px;
  height: 18px;
  border-radius: 50%;
  border: 1px solid black;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  background-color: #ffffff;
  transition: 0.3s;
  border-radius: 6px;
  padding: 16px;
}

.card-header {
  margin-bottom: 12px;
}

.card-header div:nth-child(1) {
  display: flex;
  justify-content: space-between;
}

.card-header div:nth-child(2) {
  font-weight: 300;
}

.card-header button {
  border: none;
  text-transform: uppercase;
  border-radius: 8px;
  cursor: pointer;
  font-size: 12px;
  padding: 8px;
}

.card-body textarea {
  width: 100%;
  height: 50%;
  padding: 12px;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 4px;
  background-color: rgba(235, 235, 235, 0.64);
  font-size: 16px;
  resize: none;
}

.vertical-line {
  border-left: 1px solid black;
  height: 70px;
}

/* Mobile */
@media (max-width: 767.8px) {
  main {
    grid-template-columns: 1fr;
  }

  .first-preview {
    border-bottom: 0;
  }

  .card {
    width: 85%;
  }
}

/* Tablet and Desktop */
@media (min-width: 768px) {
  main {
    grid-template-columns: repeat(2, 1fr);
  }

  .first-preview {
    border-right: 0;
  }

  .card {
    width: 60%;
  }
}
</style>
